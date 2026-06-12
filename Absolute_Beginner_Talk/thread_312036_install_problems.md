---
title: "install problems"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Stephen47 on 2006-12-03
The Ubuntu I have  working on is one I installed on an old hard drive for my son's computer. Now that I have figured out how to change the boot order I wanted I could install Ubuntu on my computer. Using the live CD I downloaded. When I got to the partitioning choices window there were three:
Erase entire disk
Use largest free space
Manually edit partition table.
I selected the second one. I clicked on continue and an error message popped up saying:"Failed to partition selected disk" I clicked ok on that and the next window was the Ubuntu will now install on selected disk box. I clicked continue and another error message popped up. This one said: "No Root file system". I clicked ok on that and it seemed to be starting to install. That is when I cancelled, not knowing what was actually going to happen and not wanting Windows wiped out.
I then downloaded the live cd file again and tried installing from it but I got exactly the same messages.
I seem to remember on the first install I was able to choose the size of the partition I wanted for Ubuntu but I was not given that option on my computer. What is going on here?

---

### Post by viper2fast505 on 2006-12-03
How do you change the boot order? I am trying to put Windows on my computer.

---

### Post by geek_Man on 2006-12-03
DANG IT, you thread hijackers! Just kidding. ;)  When you boot your computer hit F1 or F8 and navigate until you get a screen that lets you set the boot order.

---

### Post by moshuptrail on 2006-12-03
In answer the original question.
Choose the third option.
It will let you define partitions, and decide which you want to use for Ubuntu.

---

### Post by d3m0nz3y3 on 2006-12-03
I am having the same problems, only i choose the third option. After allocation memory for / and swap ubuntu installs. I am asked to restart, which i do. And when Ubuntu loads it gets stuck at, "waiting for root file system" or something like that. It never goes any furthur than this. Any ideas why?... i am installing Ubuntu on a machine which already had XP installed.

Thanks
d3

---

### Post by Stephen47 on 2006-12-04
what about "no Root file system"? Also the parttitioning tool is very vague. Why am I not given the resize option?

---

### Post by Stephen47 on 2006-12-04
hello?

---

### Post by Stephen47 on 2006-12-04
this is what came up when I ran fdisk-l:
Device Boot   Start   End   Blocks    ID System
/dev/sda1      1       5    40131     de Dell Utility
/dev/sda2      6     6689   53689230  7 HPFS/NTFS
/dev/sda3    6690    7112    3397747  db CP/M /CTOS/ ...
 what does this mean?

---

### Post by Stephen47 on 2006-12-05
bump

---

### Post by Sef on 2006-12-05
> this is what came up when I ran fdisk-l:
Device Boot Start End Blocks ID System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 6 6689 53689230 7 HPFS/NTFS
/dev/sda3 6690 7112 3397747 db CP/M /CTOS/ ...
what does this mean?

If you want to dual boot, you will need to create an ext3 partition for root and a swap partition at a minimum.   Here's [Psychocats Live CD]("http://www.psychocats.net/ubuntu/installing") tutorial on dual booting.

Linux can't install to NTFS.   The default install partition for Ubuntu is ext3.

---

### Post by Bartender on 2006-12-05
Sef - 
Can you explain the weird partitions?  I was trying to help Stephen47 but don't understand his fdisk -l.  Apparently the beginning of the HDD is taken up with some sort of Dell utility. Does that cause problems with GRUB?  GRUB wants to install at the front of the HDD, right?  Is his MBR way back at sda2?

And sda3...what the heck is that?  It's inside sda2

I've got another question...how can a person post a picture of the GParted partition map?  I've got a GParted LiveCD and have used it, but couldn't figure out how to save a screenshot.  I've seen people paste screenshots into posts so I know it's possible.  I'd like to ask the OP to do that but don't know how hard it is

Thx

---

