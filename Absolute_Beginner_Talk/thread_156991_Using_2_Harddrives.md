---
title: "Using 2 Harddrives"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by rtowsley on 2006-04-08
Hi, I am new to this. I have used the ubuntu live cd and worked with it from the cd. I would like to know if I can use this OS on a second HD while using MS XP on my main drive? If so, how do I dow this?

---

### Post by sYs^ on 2006-04-08
[QUOTE=rtowsley]Hi, I am new to this. I have used the ubuntu live cd and worked with it from the cd. I would like to know if I can use this OS on a second HD while using MS XP on my main drive? If so, how do I dow this?[/QUOTE]

Yes, it's possible, you can do this with GRUB(boot manager).

I have Ubuntu and Windows XP on the same hdd. (and it's working :p)

I think Ubuntu automatically detects your Windows XP while you're installing it(Ubuntu), but you can easily install GRUB manually too...

---

### Post by localzuk on 2006-04-08
Hi, if you use the install cd you can select which hard disk you wish to install to. Select the empty one and away you go. It will also ask you which disk to install the boot loader to - this should be the primary disk (regardless of whether it is Windows or Ubuntu disk).

---

### Post by Irony on 2006-04-08
Installing Ubuntu to a second hard drive is the easiest way to first experiment with dual boot.

This is the simplest way;

From windows first delete you second hard drive partition;

*Start > Accessories > Computer Management > Disk Management*

I can't remember the exact route, but you'll find it. Then right click on your second hard drive partition and select delete.

Put your Ubuntu install cd in the drive (assuming you have set the BIOS to detect a cd in the drive on boot up) and reboot.

When it comes to installing, select the big free space that corresponds to the second hard drive partition you have deleted - then let it automatically partition this second hard drive.

Install grub to the MBR it should detect windows. In the unlikely event you can't boot up then use windows install cd and fixmbr.

---

### Post by confused57 on 2006-04-08
I dual boot using 2 hard drives, I followed the directions by hla; in which
you install Ubuntu as the master drive and boot from it.  The windows drive is the slave drive and grub isn't installed on the windows mbr, which for me was the safest choice for the time being.  Try this thread:

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

---

### Post by ncappel1 on 2006-04-08
Please post your hardware information. Depending on the configuration, windows WILL NOT load correctly (or at all) if it is not on the Master drive. I don't know the exact details, if someone does, please elaborate.

---

### Post by confused57 on 2006-04-08
The original poster was lha and this thread may explain how to better set it up:

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

---

### Post by rtowsley on 2006-04-08
Hi, I have followed everyone advice and now have one HD - Windows and Another HD - Linex. Thanks for your help.

---

### Post by Mustard on 2006-04-08
[QUOTE=rtowsley]Hi, I have followed everyone advice and now have one HD - Windows and Another HD - Linex. Thanks for your help.[/QUOTE]

Well done. :)

---

### Post by sYs^ on 2006-04-09
Now delete your Windows and use the hdd as a storage drive for linux (lol) :p

---

