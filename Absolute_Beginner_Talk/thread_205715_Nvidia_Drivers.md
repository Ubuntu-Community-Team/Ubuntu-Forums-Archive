---
title: "Nvidia Drivers"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by underworld288 on 2006-06-28
I installed the Nvidia drivers for my MSI NX7800GT but I do not know if they are installed properly, is it possible to find out?

---

### Post by Maggot on 2006-06-28
Not sure if this command is part of the drivers, but try typing from a terminal:

nvidia-settings

Oh, and I think by default, the nVIDIA splash screen shows up.

Oh, one more way, in a terminal type: lsmod | grep nvidia
You should see something like:
nvidia               4550772  12
i2c_core               21904  2 i2c_acpi_ec,nvidia
agpgart                34888  2 nvidia,intel_agp

---

### Post by underworld288 on 2006-06-28
well a window pops up and it tells me all about my gfx card does that mean that I installed it correctly?

---

### Post by Maggot on 2006-06-28
Very bottom, NVIDIA Driver Version says what?

---

### Post by underworld288 on 2006-06-28
1.0-8762

---

### Post by Maggot on 2006-06-28
Looks good.

If you want to know for sure:   lsmod | grep nvidia

---

### Post by underworld288 on 2006-06-28
ok i did that, but what is suppose to happen. I got what looks to be info on my gfx card.

---

### Post by Maggot on 2006-06-28
You should see at least this:

nvidia               4550772  12

the numbers after nvidia may be different. That just means the module is loaded.

---

### Post by underworld288 on 2006-06-28
ok then, and yes my number is different.

thanks

---

### Post by Maggot on 2006-06-28
Another not so true test is to run the command:

glxgears -printfps

it will output how many frames per second

Depending on your card it should be a relatively high number. I have a 6800 GO, 256M (laptop)

glxgears -printfps
80859 frames in 5.0 seconds = 16171.755 FPS
89057 frames in 5.0 seconds = 17811.271 FPS
89101 frames in 5.0 seconds = 17820.078 FPS
89036 frames in 5.0 seconds = 17807.115 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by johnc4510 on 2006-06-28
try this in a terminal:
cat /proc/driver/nvidia/version
It will tell you what module is installed, that is the driver

---

### Post by underworld288 on 2006-06-28
NVRM version: NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
GCC version:  gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)



thants what i got when i typed that into the terminal, is that right?

---

### Post by johnc4510 on 2006-06-28
Yes, the 8762 is the nvidia driver.

---

### Post by underworld288 on 2006-06-28
ok so everything is install properly? if that is the case i can finally play some games.:D

---

### Post by johnc4510 on 2006-06-28
Okay, try this in terminal:
glxinfo | grep "direct"
This will tell you if direct rendering is on. It should say:Direct Rendering yes
Also try:
glxgears -printfps
And post the results for 4 or 5 averages

---

### Post by underworld288 on 2006-06-28
I have direct rendering........=D> 

5864 frames in 5.1 seconds = 1154.229 FPS
4385 frames in 5.0 seconds = 871.551 FPS
4347 frames in 5.1 seconds = 846.914 FPS
3496 frames in 5.0 seconds = 692.497 FPS
3991 frames in 6.2 seconds = 644.179 FPS
3378 frames in 5.3 seconds = 633.524 FPS
849 frames in 5.0 seconds = 168.751 FPS


their is the results.

---

### Post by johnc4510 on 2006-06-28
You should be good to go. Remember, when new kernel versions come in the updates, you may need to reinstall the driver. Other than that, enjoy.

---

### Post by underworld288 on 2006-06-28
yes finally i can play all the games i want, or at least the ones supported by linux/wine.:mrgreen:

---

