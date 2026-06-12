---
title: "Help please?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Thalaen on 2007-11-28
I posted about this issue over in installation forum, but I'm unable to get it resolved..

Specs:
Athlon 64 3200+
512 MB DDR
80 GB HDD
Chaintech VNF3-250 Mobo (nForce2 chipset, no onboard video)
GeForce3 6300GT graphics card


So, I am a complete newbie to Linux. I originally attempted to install Fedora 8.0 on the above system that I patched together; it errored out, giving an error about the kernel being killed (?). So, I wiped the drive, but still had the grub boot manager hanging around, and was unable to get rid of it.

I downloaded and installed Xubuntu 7.10 64 bit version, and had issues with it, and it was recommended that I try the 32 bit version. So, I wiped the drive again and installed the 32 bit version from the alternate installation CD image. It appeared to install with no errors.

Now, it goes through the Xubuntu loading screen to a black screen with a blinking cursor, no prompt, and will not let me type anything either; the unit is completely unresponsive - does anyone have any ideas?

---

### Post by SonicSteve on 2007-11-28
Firstly while the cursor is flashing is there any Hard drive activity? gutsy 7.10 (Ubuntu) doesn't have a boot loader splash screen while loading anymore. The longest I've seen ubuntu or it's variants take to load  was about 5mins because it had some bugs specific to the machine. 
You could try pressing "esc" when grub starts to load and see if the recovery mode will boot up. There are 2 kernel choices normal and recovery. You won't see the choices unless you press "esc".

---

### Post by Thalaen on 2007-11-28
No, there's no HDD activity. And I've let it sit there for about 30 minutes now with no response... I'll try the recovery mode per your suggestion.

---

### Post by SonicSteve on 2007-11-28
Just so you know recovery mode simply logs into a command prompt. Unless you know which commands to run it won't be alot of help. 
From my experience something sounds fishy with your hardware. It' possible that there are bugs with some of your hardware and Ubuntu, but I've seen that kind of behavior from slightly bad hard drives.

Is there someone out there who can help us with which commands to use from a terminal prompt in recovery mode. (Assuming you can even boot into recovery mode)

EDIT****
Unless you have data on the drive that you care about my further advice would be to simply try the installation again. Make sure you wipe the drive clean and use the whole thing (unless you have data that you care about). If you had set the thing up and tweaked it with all sorts of programs and settings I would recommend trying to repair but if it's already a fresh install, a few more minutes with a new installation is probably faster and better.

---

### Post by Threbus5 on 2007-11-29
I agree that you could perform a new install.

Had you considered an older 64 bit Ubuntu version?

Several threads discuss problems with Athalon machines.

---

