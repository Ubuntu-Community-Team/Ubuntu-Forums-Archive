---
title: "Gparted partitioning formatting questions"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by sfpeter on 2006-06-05
This relates to my earlier thread of getting my magneto optical drives working.  Borth drives are functional now, but when I try to format or partition them in Gparted, it just churns like it's doing something and then coughs up an error of "can not formart this partition".  It never actually seems to try writing anything to the drive.  However, if I delete a partition, I can see it write to the drive.  When I was trying fdisk I saw a note the "sectors are 2048, not 512".  

Formatting and partitioning on my Windows boxen and then using the discs in Ubuntu is just fine.  I am formatting them under Windows with 2048 sectors, os is Gparted trying to write 512, is it not really supported under Ubuntu, or what?

---

### Post by zerwas on 2006-06-05
You could try to use the GParted LiveCD and see if the problem persists. If it does so, it is a problem of (G)Parted and you should appeal to the developer of this project. :)

Greetings,
zeRwas

---

### Post by Kilz on 2006-06-05
[QUOTE=sfpeter]This relates to my earlier thread of getting my magneto optical drives working.  Borth drives are functional now, but when I try to format or partition them in Gparted, it just churns like it's doing something and then coughs up an error of "can not formart this partition".  It never actually seems to try writing anything to the drive.  However, if I delete a partition, I can see it write to the drive.  When I was trying fdisk I saw a note the "sectors are 2048, not 512".  

Formatting and partitioning on my Windows boxen and then using the discs in Ubuntu is just fine.  I am formatting them under Windows with 2048 sectors, os is Gparted trying to write 512, is it not really supported under Ubuntu, or what?[/QUOTE]

The only thing gparted ever did for me was cause me to have to reformat a drive.

---

### Post by Jagot on 2006-06-05
You could try DiskDrake, which a lot of people seem to recommend over Gparted:

[http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake](http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake)

The easiest way to obtain it is in the PCLinuxOS LivedCD:

[http://www.pclinuxos.com/](http://www.pclinuxos.com/)

---

### Post by catlett on 2006-06-05
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) This is the link for the gparted live cd. I have never had a problem and have been recommending it with good results.
The big difference between gparted in ubuntu and gparted live is that gparted live runs off of a live cd. Therefore your hard drive is not mounted and the operations can be applied right there and then.
It is a small download, only 30mb, so you can get it quickly. It's easier than downloading an entire distros live cd just for the partitioner. The interface is nice. You boot right to gparted but you are actually in xorg with a fluxbox window manager.
Just thought I'd throw it out there. It's quick enough that you might want to try it and if it doesn't, then download an entire live distro and try that. But I think gparted live will do the trick.

---

