---
title: "Signal gets cut off after &quot;Kernal Alive&quot; message."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Delacroix on 2007-06-01
Hi guys, I'm running Ubuntu 64bit now. Here is my full story. First I downloaded the Desktop version of Ubuntu and burnt it onto a CDR. I booted from the CD and got to the Ubuntu menu with the Intallation options and stuff. 

I selected the first option which was to Start or Install Ubuntu. After the Kernal Alive message the signal from the video card to my monitor got cut off. Meaning my monitor was displaying an orange light and giving out a No Signal error and my whole computer just stays like that. So i rebooted and chose the 2nd option which was the safe mode. Same outcome. No Signal to my monitor after the Kernal Alive Message.

So I tried downloading the alternate install CD instead and burnt it to another CDR. This time I was able to install Ubuntu to my HDD. But when I rebooted and pressed the first option to start Ubuntu I get the same cut off signal message. I rebooted and used the recovery mode and typed startx and it gave me the same problem as well.

So after that I installed fglrx and manage to boot into Ubuntu with the startx command in Recovery Mode. So I thought ok everything is fine now until I found out I cannot adjust any system stuff because I was using Recovery mode or something. So I rebooted in order to boot into Ubuntu using the first option. But after selecting the first option in Grub Loader it gave me the same error as before. After the kernal Alive message my computer would just sit there without any activity and the signal to the monitor gets cut off. 

Anyone know what's going on here?

Here are my system specs.

AMD Athlon 64 X2 3800+ Stock
Biostar Tforce4 SLI
ATi Radeon X800GTO with fglrx driver installed
1024MB Kingston Value RAM
Ubuntu is installed on a Maxtor 40GB HDD with no swap file.

---

### Post by Delacroix on 2007-06-01
No ideas?

---

### Post by Delacroix on 2007-06-01
Bump

---

### Post by jonward0690 on 2007-06-01
Have you thought about just using the 32bit verson of ubuntu.I have a 64bit dual processer and I just run 32bit because the 64bit setup is so funny.

---

### Post by Delacroix on 2007-06-01
> **jonward0690 said:**
> Have you thought about just using the 32bit verson of ubuntu.I have a 64bit dual processer and I just run 32bit because the 64bit setup is so funny.

Yeah, I'm in the midst of downloading the alternate installation cd 32bit. Will report back after I installed it.

---

### Post by rayh059 on 2007-06-02
Same thing on mine but I started with the 32 bit version.  The alternate installed well, but now I get the same "loss of signal" symptoms.   It would appear to be a video driver issue, I'm not sure where to go from here.

---

### Post by Delacroix on 2007-06-02
The 32bit works fine for me now. Not sure what's wrong with the 64bit version. I had a bit of a trouble with the 1st 32bit install where during the loading screen the OS would do a forced scan or somesort and gave an error at the end and auto reboot itself. I tried booting again and it gave me a black screen after the loading screen. 

I got pissed off and reinstalled it but changed a few settings. I'm running ReiserFS with the Bootable Flag set to No.

Previously with the 64bit and the 1st 32bit install I was using ext3 with the Bootable Flag set to Yes. Now sure whether is this the cause of the error or not but I just want to inform everybody here what I did.

---

### Post by Tylon_Foxx on 2007-07-15
if you use GRUB, then you can look in my example of the menu.lst

close to the bottom, just after ## ## End Default Options ##, the title, root and the kernel is listed.

I run the ubuntu Feisty 64-bit on the lastest kernel (2.6.20-16)

but under the kernel part, you will see something like:

> kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=45f4fb35-77f0-419d-9417-9cd84634459f ro quiet splash locale=da_DK vga=794

the "locale=" part is just for showing stuff in the Danish language, since i'm Danish

but the "vga=794" part is what you need. If it isn't there, then add it. I presume that your monitor is fairly new and can show the 1280x1024 resolution.

vga=794 will start up ubuntu with a default setting of 1280x1024 with 16 bit color depth, using 795 instead will use 24-bit color depth.

since I have a Radeon X800GTO too, this should work :)

---

