---
title: "Dual booting with 2 HDs"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-19
I want to configure my PC with two hard drives and install Windows XP on one HD and Ubuntu on the other. How do I set it up so I can select the OS I want to boot ? Do I need to hit the F2 key at start up and select the boot drive or is there an easier more convenient method ?

Regards,
grofaz

---

### Post by ketiko on 2005-07-19
Do you have Grub or Lilo installed?  They are programs that let you select various OS during bootup.  If you installed Ubunutu you will have probably installed Grub.  In you Bios, which drive do you have selected to boot from?  Does it just boot straight up to windows?

---

### Post by grofaz on 2005-07-19
I have Grub installed. Ubuntu is the default OS when I power up, I have to scroll down to select Windows if I want to boot Windows instead of Ubuntu. But from what I understand the BIOS boots from HD1 so if Ubuntu is installed on HD2 and the MBR is on HD1 how do you set things up to allow a choice of OS at power up ? I have no idea what I'm talking about, hence this thread.

---

### Post by Kyral on 2005-07-19
Uhh, trust me, the way its working right now is the way it should be. 

Don't go messing in the BIOS unless you a) have your Motherboard manual on hand or b) know what you are doing, because you can fubar your computer beyond belief (I should know :))

---

### Post by GTvulse on 2005-07-19
[QUOTE=grofaz]I have Grub installed. Ubuntu is the default OS when I power up, I have to scroll down to select Windows if I want to boot Windows instead of Ubuntu. But from what I understand the BIOS boots from HD1 so if Ubuntu is installed on HD2 and the MBR is on HD1 how do you set things up to allow a choice of OS at power up ? I have no idea what I'm talking about, hence this thread.[/QUOTE]
 You are correct in thinking that Windows likes to be the first OS on the first drive. But GRUB can fool windows into booting from a slave drive. Read [chapter 4 of the GRUB manual](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html).

---

### Post by grofaz on 2005-07-19
OK, I'll read chapter 4 of the Grub manual. Thanks for the tip !

---

