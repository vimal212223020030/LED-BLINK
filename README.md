# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
  ![WhatsApp Image 2025-10-29 at 07 38 27_98dc18a2](https://github.com/user-attachments/assets/8b8d9f61-3c23-483b-a692-7ea4ae1613b5)

2. Click **File → New STM32 Project**.
![WhatsApp Image 2025-10-29 at 07 53 27_e367da24](https://github.com/user-attachments/assets/188bf355-963c-43fb-a323-3143364ff7e6)
![WhatsApp Image 2025-10-29 at 07 53 45_ff3a737e](https://github.com/user-attachments/assets/609fbbd5-45bc-4c2f-b703-f5a7fca0815e)


3. Select the **target microcontroller** or board and click **Next**.
   ![WhatsApp Image 2025-10-29 at 07 54 02_beff69be](https://github.com/user-attachments/assets/d1f417f6-0786-43e1-af6a-02ea1abc4ffb)




4. Name the project.
  <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/53a5c2c8-b044-4480-8c3d-055bd8010351" />


5. The corresponding `.ioc` file will be generated automatically.
  ![WhatsApp Image 2025-10-29 at 07 54 34_3b0373ff](https://github.com/user-attachments/assets/14b3f83b-8fbc-470c-bba9-a4ae481a0577)

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  ![WhatsApp Image 2025-10-29 at 07 54 53_183d6d35](https://github.com/user-attachments/assets/69fa1b91-e38a-44d4-a43f-781ba76dbab6)



7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 ![WhatsApp Image 2025-10-29 at 07 55 21_438c5f09](https://github.com/user-attachments/assets/25c6605f-55a3-4547-9dbe-e622ecaff1ff)

8. Edit the generated main program as required.
![WhatsApp Image 2025-10-29 at 07 55 51_914fc2d3](https://github.com/user-attachments/assets/1b34cf56-be85-4ce5-8389-094253db6360)

9. Click **Project → Build All**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/264cd0a8-3e96-4668-822e-838ecfafc527" />
![WhatsApp Image 2025-10-29 at 07 44 57_39be0e95](https://github.com/user-attachments/assets/6ad83d20-983b-4d92-82c0-7877b4b09421)

10. Link the **HEX file** using the post-build process.
   ![WhatsApp Image 2025-10-29 at 07 45 35_482435ee](https://github.com/user-attachments/assets/bff545d5-d2aa-41e0-9a83-b5fce65e53f0)
 

11. Click **Debug** and connect the **STM Nucleo Board**.
  ![WhatsApp Image 2025-10-29 at 07 45 56_dcdcc31d](https://github.com/user-attachments/assets/831ecc94-6187-4663-b33f-45008e609170)
![WhatsApp Image 2025-10-29 at 07 46 35_87a6d573](https://github.com/user-attachments/assets/e8c80b79-e3f5-4143-b203-efdc2f017337)

13. Click **Run** to execute the program.
    
---

### 💻 **Program**
```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

![WhatsApp Image 2025-10-29 at 08 08 14_165bc418](https://github.com/user-attachments/assets/a1fc23c5-28da-4e78-a753-8b8bd7bb13e0)


CASE 2: LED OFF

![WhatsApp Image 2025-10-29 at 08 08 15_3566ea99](https://github.com/user-attachments/assets/413a9889-c04b-48b3-99eb-e87b9cd77ca7)

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
