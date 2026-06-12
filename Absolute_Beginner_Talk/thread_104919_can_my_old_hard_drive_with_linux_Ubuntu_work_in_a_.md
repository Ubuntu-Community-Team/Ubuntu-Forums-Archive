---
title: "can my old hard drive with linux Ubuntu work in a new computer system"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by lignito on 2005-12-17
can my old hard drive with linux Ubuntu work in a new computer system?

---

### Post by bscbrit on 2005-12-17
I would be most surprised if the drive didn't work but it will not have the correct software drivers for your new computer installed.  Although it might boot first time - but might not - you will probably find that sound, network, video etc would all need tweaking to make them run properly.  If you simply want to save your data then you could install your old drive in the new computer as a slave drive (ask if you want to know more about this) and perhaps copy the data to your master drive.  I assume that your master is a Windows drive (probably XP?).  However, you will have more success by mounting your old drive as a slave and re-installing ubuntu onto it, making your new system a dual boot system with both windows and ubuntu.

Of course, simply installing it as a slave drive will not enable you to boot from it, but it can be made to be bootable.

---

### Post by lignito on 2005-12-17
I thought that Ubuntu detects hardware at boot time...
The reason that I want to use this disk on a new computer is because I have management software of my buiness(invoices,etc) and it is very difficult to get it to work...the program name is EVARISTO. Is there a simple way to get this to work in a new machine? Thank you for any help any way.:)

---

### Post by kosmic on 2005-12-17
yes EVARISTO is a pain in the ass to configure, Linux detects your hardware at boot times, so probably it will work out of the box, unlesss you have any new hardware that is unsuported by linux

---

### Post by gw90se on 2005-12-17
This is from another thread about the same topic.
> It will boot as far as the console, as X will crash due to different hardware. at this point, login, and run:

$sudo dpkg-reconfigure xserver-xorg

answer all the question to the best of your knowledge, and try running gdm.

Hope this helps.

---

### Post by bscbrit on 2005-12-17
If your new computer does not already have a hard drive in it, then putting your old drive into it as the master will make your computer boot from the ubuntu drive.  BUT, as already stated, you will need to modify certain settings to get the video, sound etc working.

If you already have a master drive in your new computer, then adding the old drive as a slave will not have any effect.  You will be booting from the master drive and it does not know about the new slave drive that you have just added. Ubuntu is on the slave drive in this instance and so will never get to run - hence it cannot detect any hardware.  If you want the ubuntu drive to be fitted as a slave, then you will have to change the way your new computer boots so that it knows about the slave drive and gives you the option from booting from the master drive or the slave.  This can be done but I'm not going to go into details unless that is what you wish to do.

---

