---
title: "XP on USB?"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by kyotodude on 2005-07-08
I just bought an external hard drive to hold Windows XP.  However, while I can add an entry to the "menu.lst" file in /boot/grub, whenever I go to boot to Windows on USB, it does not boot to Windows, but displays the text of configuration of the partition in menu.lst.  This is similar to what happens when I boot Windows on my main hard drive, but it only appears for a few seconds, before Windows boots.  Any suggestions on how to make this work?

Edit:
My menu.lst config file 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
map (hd0) (hd1)
map (hd1) (hd0)
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by apollo2011 on 2005-07-08
I don't think you can boot XP off an external USB hard drive...From what I find on the Internet, it would only be bootable if you took the hard drive out of its case (yes inside it is a normal desktop hard drive) and mount in your PC.  I know you could put Ubuntu or any other Linux on an exteran hd but I don't think Windows allows you to do that.

---

### Post by Bl0wn2b1ts on 2005-07-08
Hi,

You may have to load the DOS drivers first to get your machine to recognise it.

Not an expert on this but thats prob where the add command on GRUB comes in??

hope this helps ;-)

Bl0wn2b1ts

---

### Post by apollo2011 on 2005-07-08
Grub shouldn't be the problem, because Ubuntu can be installed on an external hard drive.  The problem must be either in a bad command in the menu.lst or the fact that Windows XP cannot be installed on an external hard drive.  Have you been able to run XP off that external drive before?

---

### Post by kyotodude on 2005-07-09
Nope, although I can access it from both Ubuntu and XP on my internal drive, and it is an exact copy of my internal XP partition.

---

### Post by N'Jal on 2005-07-09
I know that you can store a windows file system on a USB drive but i think windows has to be booted before it'll do this, to check the integrity of drives i once worked with a guy that had a USB kit, it turned any IDE drive into a USB drive and acted like a USB memory stick, you then plugged the USB drive into a booted windows partition and could viem the files etc.

---

### Post by apollo2011 on 2005-07-10
Yes, as I said before, I am pretty sure that Windows cannot be booted off an external hard drive.  I have heard before that although Linux can be put on a USB flash drive, Windows cannot, and would be too big anyway for any flash drive.

I would recommend that if you want one operating system per hard drive, that you keep XP on the internal hard drive and put Ubuntu on the external hard drive.

---

### Post by mArVi on 2005-07-10
Would you recomend two hard drives instead of using one if you plan on using both Windows and Linux? What is a good size external hard drive for Linux? 

Marvi

---

### Post by apollo2011 on 2005-07-10
[QUOTE=mArVi]Would you recomend two hard drives instead of using one if you plan on using both Windows and Linux? What is a good size external hard drive for Linux? 

Marvi[/QUOTE]
 That all depends on how big the drive(s) you have are.  A Ubuntu system might only be 2GB minimally so you would only need a partition slightly bigger to use it.  But you would probably have a system closer to 5GB and I would recommend a partition somewhere between 10 and 20GB (mine is 40GB but that is very unnecessary).  You might also need a vFAT partition in between Windows and Linux to transfer files, since Ubuntu can't write NTFS securely.

---

