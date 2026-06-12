---
title: "Failure to install"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Robbyx on 2006-08-21
Because of my use of the Asus P5B MB with the Pentium 4 I have found it impossible to install Ubuntu using the CD drive. Ub starts from the CD and then says it can not find the CD.

I have Win2k on the machine. Is it possible to install Ub from a hard drive?  


Robin

---

### Post by seshomaru samma on 2006-08-21
If I understand you correctly (u managed to boot the CD but after a while the installation process says it can't find the CD drive) I have encountered this problem before
It was a hardware problem and I solved it be going into the CMOS settings - but I can't remember what I did. Try to play with the CMOS setting for a while. If this doesn't help ,then:
Do you get any errors on your Windows 2k?
Do you have a floppy drive?

---

### Post by Robbyx on 2006-08-21
I can not anything obvious in the bios. I do have a floppy drive.

Robin

---

### Post by sacater on 2006-08-21
try going through bios all the way, checking CMOS, hardware specs etc, if that dosnt work using the cd in other os's and see if it can be read, if it can i have no idea, im hoping its a cd problem

---

### Post by Robbyx on 2006-08-21
It is not a CD problem. There was another thread dealing with this problem. It is connected with an absence of Atapi drivers in the installation program and the absence of atapi drivers built into the bios of this type of pentium 4. That is why I asked if there other ways of installing Ab.

---

### Post by seshomaru samma on 2006-08-21
Robbyx
if i'm not mistaken you can update your bios
if not please try [this]("http://btmgr.webframe.org/")
or [this]("https://help.ubuntu.com/community/SmartBootManagerHowto")

---

### Post by thotz on 2006-08-22
> **Robbyx said:**
> Because of my use of the Asus P5B MB with the Pentium 4 I have found it impossible to install Ubuntu using the CD drive. Ub starts from the CD and then says it can not find the CD.

I have Win2k on the machine. Is it possible to install Ub from a hard drive?  


Robin

Please, Robbyx, could you file a bug report on bugs.ubuntu.com with the error? We can only hope that this driver will then be added in the Ubuntu kernel.

---

### Post by Robbyx on 2006-08-25
I tried the advice to create a special boot disk on a floppy. The program did not see the CD drive. Any ideas why not and what  I should do next?

---

