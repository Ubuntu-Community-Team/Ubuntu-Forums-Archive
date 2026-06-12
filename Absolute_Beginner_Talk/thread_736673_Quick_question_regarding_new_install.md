---
title: "Quick question regarding new install"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Propaghandi on 2008-03-26
To get to the point:

200GB IDE Master, currently drive J in Windows (This is the drive I want to install Ubuntu on)

300GB SATA, drive C: currently runs Windows XP.

500GB SATA2, storage drive, drive D:

I want to install Ubuntu onto it's own drive. If I bootup with the Ubuntu CD and install it on what is now drive J:, will it affect my Windows install?

In short, when I startup my system, I'd like to hit F11 to get to my BIOS boot selection screen, and choose either the Windows XP drive or Ubuntu drive depending on what OS I want to use. I don't want to mess with menus or altering boot lists or whatever. I want my OS's to be separate and completely ignorant of each other. 

Is this possible with my current setup? 

During Ubuntu install, should I select to install the boot loader onto the drive I'm installing it on?

Thanks in advance. :) I'm very excited to start using Ubuntu!

---

### Post by northern lights on 2008-03-26
It won't screw with your windows at all, unless you choose to alter that partition/drive during the installation process.

The Ubuntu install install the GRUB bootloader once it's done. It will right away have a Windows entry. No hitting Fkeys involved...

This might be useful:
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by codeslicer on 2008-03-26
What's wrong with GRUB? It works well.

Windows will not be affected if you install Ubuntu on to an empty drive, but it may still try to "detect" the new operating system. If you see a Windows Filesystem Check screen, that means you have installed Ubuntu correctly and Windows is just checking it's new buddy ;)

If you install the bootloader, you probably want to install it into the C drive with Windows, as that drive is already bootable. This might partially override the existing Windows bootloader, but don't worry it's not a big problem. During setup Ubuntu detects all existing operating systems.

---

### Post by Propaghandi on 2008-03-27
I ended up installing 8.04 since, for some reason, 7.10 hangs. I tried a CD made from an ISO image (CD check reported no errors) and also a distribution CD from Linux Format magazine. Both hung up. 

Using the Hardy Heron build got the install going no problems. 

I installed it to the hard drive I mentioned and it's boot loader remained separate from my C: drive. 

So when I boot up, I hit F11 for boot up options, pick my Ubuntu drive, and I'm off and running. Complete separation of OS's which was my goal. 

Thanks for the nudges.

---

### Post by stefangr1 on 2008-03-27
If you want to do that, you have to disconnect (or disable in the bios) the harddrive that has windows on it. In that case you can switch between the different operating systems by altering the boot order in the bios.

If you're not going to dual boot on a regular basis (you want to keep windows, but already know you're going to use it less than once a month, for example), this can be a good option. This is because the chance that the mbr is messed up is slightly larger in dual boot systems. Also, when you move disks to other computers, the system will boot normally only when there's an mbr on it.

---

