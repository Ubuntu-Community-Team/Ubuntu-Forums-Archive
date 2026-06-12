---
title: "Windows is ignoring part of my hard drive"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-11
I'm STILL trying to install windows, and now (after messing around with the bios) it is at the point where i can choose which hard drive partition to install it on.

the only problem is that it only gives me one choice: My ubuntu partition.

i've tried using just free space, using nfts, and using ext2 (same as ubuntu) formats, but it all produces the same result. windows can't read it.

anyone know how to configure a partition?

---

### Post by seshomaru samma on 2007-06-11
did you create a partition for windows?
try a fat32 
what's your sudo fdisk -l?

---

### Post by eddieb on 2007-06-11
Windows MUST be on the 1st partition of the 1st hard drive.  NO buts!

---

### Post by Tyke91 on 2007-06-11
you mean, 

The first partition created

or

the first partition in the order of the partitions?

because there are people who have succeeded in installing windows second (it ruins grub, but im comfortable reinstalling that :p)

---

### Post by Tyke91 on 2007-06-11
after reading some of the words on the blue screen... it seems as if it is ONLY looking at the partition in bus 0

Ubuntu wasn't originally in bus 0 (i think windows was) so how do i create a partition in that bus?

---

### Post by jcronkhite on 2007-06-11
Can you give us the exact specs?  How many drives do you have?  What interface is it/are they?  Maybe download the Gnome Partition Editor Live CD at [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") and see what the status of your partitions are.  Hope this helps your troubleshooting!

---

### Post by Tyke91 on 2007-06-11
I've only got one hard drive

Model: ATA SAMSUNG HD 160JJ/
Size: 149.01 GB
Path: /dev/sda

DiskLabelType: msdos
Heads: 225
Sectors/Track: 63
Cylinders: 19452
Total Sectors: 312496380


ive been using gparted (livecd) to manipulate this thing... so far its gotten me this far :)

any other system specs?

---

### Post by darren1270 on 2007-06-11
Maybe this will work for you.... Do you care about loosing any data????  If not I would recomend using Killdisk to wipe everything from your drive... you can get it here [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm) the free version only supports one pass but it worked for me.  Next you need to install windows first... when you get to the screen about partitions you can choose how much space you want for windows... say 100Gig.... then once you have windows installed you can use the ubuntu live cd and just choose the continuious free space option....It worked this way for me.


BTW Download the .iso for killdisk

Good Luck
Darren

---

### Post by jcronkhite on 2007-06-11
You could even use your live GParted disc to delete all partitions, then create a new windows partition during Windows setup (NTFS is fine, and recommended for better Windows "Security").  Once Windows is setup, Boot from the Ubuntu 7.04 Live CD and double click on the installer on the desktop.  When Ubuntu asks you about the partition information, select the option to use the largest empty space on the hard drive and away you go.

If you need to backup your data first, you can boot from the Ubuntu Live CD, then mount a USB stick (if it will fit your data) or an external USB hard drve, then copy whatever data you have to it before you wipe everything out.  Keep us posted.

---

### Post by Tyke91 on 2007-06-11
the thing is, i care about losing data :)

mostly it's all my music... it would take over a week to get my entire collection back.


i guess i'll just go out and buy an external drive.

---

### Post by santy_kushwaha on 2007-06-11
if u are thinking of buyin the eexternal hard drive then upload all the files from ubuntu to it and reinstall everything thats easier then jugling around

---

### Post by marco123 on 2007-06-11
> **Tyke91 said:**
> the thing is, i care about losing data :)

mostly it's all my music... it would take over a week to get my entire collection back.


i guess i'll just go out and buy an external drive.


Highly recommended.

 Best thing I ever bought was an external HD.  I can now do whatever I want/install and reinstall at the drop of a hat, I just unplug the external and off I go.:D

---

