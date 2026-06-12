---
title: "Resolving Display Issues with Radeon HD 4850 on iMac27 Mid-2010 in Ubuntu 22.04.3"
date: 2023-12-17
forum: Apple Hardware Users
---

### Post by kimyendick on 2023-12-17
I am facing a display issue on my iMac27 (mid-2010 model, iMac11,3) with a Radeon RV770/M98L (Mobility Radeon HD 4850) graphics card after installing Ubuntu 22.04.3. Below is the detailed description of my problem and the troubleshooting steps I have taken:



Issue Description:
Booting without nomodeset parameters results in a black screen on the built-in display. When an external monitor is connected, it functions correctly, but the built-in screen shows white lines on a black background. If I add nomodeset to the GRUB parameters, everything works fine but no used graphic card. However, adding acpi=off in GRUB makes the built-in display work, but then USB controllers stop functioning. Troubleshooting Steps Taken:
Ensured xserver-xorg-video-radeon driver is installed and up to date.


Conducted system updates and upgrades. 

System Specifications:
iMac Model: iMac27, Mid-2010 (iMac11,3) 
Graphics Card: Radeon RV770/M98L (Mobility Radeon HD 4850) 
Ubuntu Version: 22.04.3 

I am seeking assistance to:
How to resolve the black screen issue on the built-in display without compromising USB functionality? Find the best configuration for my Radeon HD 4850 under Ubuntu 22.04.3. Any advice, troubleshooting tips, or insights into resolving these issues would be immensely appreciated. I can provide further details if needed.
Thank you for your time and help!

---

### Post by howefield on 2023-12-17
Thread moved to the "*Apple Hardware Users*" forum.

---

