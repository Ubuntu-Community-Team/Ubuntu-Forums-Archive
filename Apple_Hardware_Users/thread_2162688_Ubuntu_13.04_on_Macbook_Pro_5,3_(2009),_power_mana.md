---
title: "Ubuntu 13.04 on Macbook Pro 5,3 (2009), power management troubles, ACPI=off"
date: 2013-07-15
forum: Apple Hardware Users
---

### Post by gutigreg on 2013-07-15
Hi all!

after few years working with Mac OS X on my Macbook Pro 5,3 from 2009, I decided to go Ubuntu again. After reading stuff on forums, I managed to install Ubuntu 13.04 on the internal drive, using the AMD64+Mac iso. I had to specify **ACPI=off **and **NOMODSET** while booting from the live CD. The installation went ok, I rebooted and had to connect with an ethernet cable to upload the wifi driver and the nVidia driver. 

Now my system runs ok (I'm surprised but I do enjoy Unity!), except for one big trouble: I can't use ACPI management, it freezes the desktop after few minutes. I have to keep the **ACPI=off** parameter in */etc/default/grub* configuration file. So the computer feels a bit warm after one hour or two and I don't like it.

If I delete the parameter from the file, I can see the battery indicator, suspend/hibernate work, the system goes on suspend and the apple at the back of the screen shuts off when I close the screen. But the systems lasts for few minutes before it freezes, and I must long press the power button to shut down and reboot.

I tried some other parameters instead of ACPI=off :

**ACPI_OSI=Linux **: ACPI is managed (I see the battery indicator, etc.), the computer runs smoothly for 20 to 40 mn (more or less), then it suddenly freezes again, whatever stuff I'm doing (browsing with Chromium, watching a video with Totem, working on some audio file with Audacity...).

**MAXCPUS=1** : The computer seems to work flawlessly for few hours, but it's less powerfull as it runs with only one CPU instead of two, and in the end it freezes (just tested 2 times so I'm not sure... Anyway I don't want to run with only one CPU).

I've been asking questions on Askubuntu and browsing forums and blogs with no success yet. See my Askubuntu report [here]("http://askubuntu.com/questions/317473/acpi-and-macbook-pro-5-3-ubuntu-13-04/318877#318877"). I tend to think that there's a problem somewhere between GRUB2 and the handling of settings by the kernel... I read about rEFIt for bootloading Macs but as far as I understand, it's intented for dual boot purposes and I only use Linux on this computer.

My Ubuntu system: fresh install of 13.04, kernel 3.8.0.26, graphic driver is nvidia 313-updates. Running Unity and Cinnamon.
I tried nvidia 310 ("tested, recommanded" driver) and Nouveau driver, same troubles. Nouveau driver is very sluggish anyway.
Processor: Intel Core 2 Duo CPU P8800 @ 2.66 GHz
Graphic card: GeForce 9600M GT/PCIe/SE2

Please provide help!

Greg
Paris, France

---

### Post by gutigreg on 2013-07-15
Update: Tried with these other parameters (one a a time) in GRUB2 and reboot, same trouble applies (general freeze few minutes after accessing Unity desktop): **acpi=noirq** **pnpacpi=off** **pci=nommconf** **pci=nocrs**

So for now I'm stuck with acpi=off, which is boring because I don't have battery management and I can't suspend/hibernate. Poor me :(

---

