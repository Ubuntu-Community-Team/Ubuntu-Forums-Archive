---
title: "Install Ubuntu 7.04 without touching MBR"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by tractordriver88 on 2007-05-20
I just installed Ubuntu 7.04 from the Live CD and it will still only boot to Windows XP.
I have two hard drives. A SATA drive for Windows, and a second hard drive, ATA for Ubuntu. Now, Partition 1 is for data that I have saved from Windows and Partition 2 is for Ubuntu (It used to have Vista RC2, but it is about to die and I'm not paying to keep it!) From what I have read, it sounds really dangerous to be allowing Ubuntu to change the MBR. What I want is the bootloader to present the option from the Windows Bootloader to boot to GRUB. That's what sounds safest, but I have not come across an article on how to do that yet.
Help is appreciated!
A friend got me interested in Ubuntu and I want to give it a try.

---

### Post by Rui Pais on 2007-05-20
> **tractordriver88 said:**
> ,,, From what I have read, it sounds really dangerous to be allowing Ubuntu to change the MBR. What I want is the bootloader to present the option from the Windows Bootloader to boot to GRUB. That's what sounds safest, but I have not come across an article on how to do that yet.
....
Hi,
in fact is the other way around.

Installing Grub on MBR is usually safe (and relatively easy to recover in case of anything goes wrong) and at least till XP, and i think Vista too, Windows bootloader only allow Window system to boot.

---

### Post by tractordriver88 on 2007-05-20
OK, How would I install the GRUB without screwing up XP? I can only boot to the LIVE CD though.

---

### Post by Rui Pais on 2007-05-20
> **tractordriver88 said:**
> OK, How would I install the GRUB without screwing up XP? I can only boot to the LIVE CD though.

if you installed Ubuntu thats probably done already. But on the MBR of the wrong hd. Test by boot your computer and evoke the menu to choose the media you want to boot from (usually key F8 or F12). Coose boot from the ATA drive. 
If it boots grub from there, is installed :)

How to make definitely? 
You can set that option on Bios setting (and you keep XP boot loader untouched), or follow the instruction here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Read specially the part: [Changing the Disk that Grub is installed to]("https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668").

Good luck.

---

### Post by skyhopper88 on 2007-05-20
You can install grub on your ATA that has only Ubuntu. Then set that drive to boot first. Grub will be able to see Windows but won't touch the mbr. It's what I did.

---

### Post by tractordriver88 on 2007-05-20
Alright, I'll give it a roll and report back in a while.

---

### Post by tractordriver88 on 2007-05-20
Hey! It works!
Thank you very much Skyhopper.
I just set my Bios to boot to my ATA rather than SATA drive.
Thanks!

---

