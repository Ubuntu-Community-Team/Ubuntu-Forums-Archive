---
title: "[SOLVED] Lost root password"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by AndyCinDallas on 2007-07-27
My wife forgot her user ** and** root password for Ubuntu 7.04 - would she have to reinstall from scratch or is there a recovery-method?

---

### Post by aysiu on 2007-07-27
There is no root password.

You can reset her user password, though, by booting into recovery mode and typing ```
passwd *username*
reboot
``` where *username* is her actual username.

---

### Post by Blutack on 2007-07-27
Edited- aysiu said the same thing but better

---

### Post by AndyCinDallas on 2007-07-27
Thanks, guys - will try that immediately

---

### Post by AndyCinDallas on 2007-07-27
That worked perfectly - thanks, guys. I hadn't dared to hope it would be that easy - you're lifesavers :)

---

### Post by djchandler on 2007-07-27
> **aysiu said:**
> There is no root password.

You can reset her user password, though, by booting into recovery mode and typing ```
passwd *username*
reboot
``` where *username* is her actual username.

I didn't think you can reset the administrator's account password without being root or su, which would require the original password. I've not had this come up before. I understand being able to do this as root or su, but not if you are the administrator and have forgotten your administrator account password. It seems to me that anybody could boot your computer into recovery mode, gain root or su status, and have access to everything. What am I missing here? It must be that she wasn't the administrator to begin with. I don't recall that being clearly stated.

DJ

---

### Post by FleetAdmiral74 on 2007-07-27
> **djchandler said:**
> I don't think you can reset the administrator's account password without being root or su, which would require the original password. Am I wrong about this? I've not had this come up before. I understand being able to do this as root or su, but not if you are the administrator and have forgotten your password.

DJ

It was my understanding she was a user, not administrator.

---

### Post by Blutack on 2007-07-27
That only works using the recovery boot mode of ubuntu from the grub menu.  Hence, I alter my menu.lst to password all grub options other than the default boot.  Its still not hugely secure but that + a bios password and HDD first in the boot list does the trick for me.

---

### Post by aysiu on 2007-07-27
> **djchandler said:**
> I didn't think you can reset the administrator's account password without being root or su, which would require the original password. I've not had this come up before. I understand being able to do this as root or su, but not if you are the administrator and have forgotten your password. It seems to me that anybody could do this, gain root and alter everything. What am I missing here? It must be that she wasn't the administrator to begin with. I don't recall that being clearly stated.

DJ

> **FleetAdmiral74 said:**
> It was my understanding she was a user, not administrator. It doesn't matter whether or not she is a user or an administrator. Booting into recovery mode makes you root, so you can change the password of any user with the command I gave earlier.

Of course, if another user had been administrator, the OP wouldn't have had to boot into recovery mode. If he, for example, were a sudoer, he could have logged into his own account and changed her password by going to System > Administration > Users and Groups or typing this command in the terminal: ```
sudo passwd *username*
``` where *username* is his wife's username.

---

### Post by nichipet on 2007-07-27
I understand DJ's concern, that does seem to make it easy for anyone with physical access, and knowledge of the procedure, to become root and wreak havoc. Blutack's approach is nice, but if the user forgets their password, then recovery mode is not available anyway (unless it's a different password, naturally). So, is there a way to protect a computer against this? Of course, I suppose this situation may support the argument of a separate root user being a good idea.

N.B. I started on Linux years ago, took a break, came back by trying Ubuntu. No "real" root user or root password was very strange to me!

---

### Post by aysiu on 2007-07-27
If someone has physical access to your computer and malicious intent, then your computer will be compromised. If you want to slow the person down, you can chain the computer to the floor, block the CD-ROM drive from ejecting, seal the computer (so that screws won't matter), set up a BIOS password and a Grub password, and remove the recovery mode entry from Grub.

The best thing to do, though, is make sure people you don't trust stay physically away from your computer. But recovery mode is necessary precisely for situations like these (my wife forgot her password).

---

### Post by Blutack on 2007-07-27
Of course, if someone has physical access to the machine they WILL be able to access the data somehow (unless you start encyption mounting drives).  My method at least requires them to crack open my laptop.  You can stop grub generating recovery entries but if you are knowlegable you can use grub to add the required paramenters (specifically I believe it boots to runlevel 2) to the end of the standard kernel line.  To be honest, if anyone really wants the data they will have it, I have a combination of irrational paranoia and a flatmate with a penchant for setting a certain image of a female in a bathtub as backgrounds/home pages.

---

### Post by nichipet on 2007-07-27
Of course all systems are ultimately insecure, if someone is determined to get in, they will. But at least in a standard boot the default for sudo requires the user's password after x seconds of not being used. It's not much protection, but it's something. But what a nice option to just reboot, select the recovery mode and destroy the system without knowing any passwords.

---

### Post by aysiu on 2007-07-27
> **nichipet said:**
> Of course all systems are ultimately insecure, if someone is determined to get in, they will. But at least in a standard boot the default for sudo requires the user's password after x seconds of not being used. It's not much protection, but it's something. But what a nice option to just reboot, select the recovery mode and destroy the system without knowing any passwords.
Well, there's always a delicate balance between security and convenience. Ubuntu is designed to give you security against online threats, but it is not designed to guard against physical access threats. I would not want to try to give people online support for forgotten passwords if there were not recovery mode.

---

### Post by bsharp on 2007-07-27
> **Blutack said:**
>  I have a combination of irrational paranoia and a flatmate with a penchant for setting a certain image of a female in a bathtub as backgrounds/home pages.

Dude, that pic is so wrong....I would kill anyone who did that to me.

---

