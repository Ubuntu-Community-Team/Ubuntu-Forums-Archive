---
title: "What are &quot;devices&quot; in Gparted?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by ccclairee on 2007-08-18
trying to partition my hardrive before I install.

I thought I had a 80 GB hardrive, but there is only 37 GB on my C: drive, another 37 + GB on my E: drive. In  Gparted, it only shows about 37 GB of space, but there are two "devices". One called dev/hdb1 and one called dev/sda. What are devices? Also, in Gparted it only shows one big partition, but shouldn't there be two partitions; C and E? Or do I have two hardrives?  I'm so confused.

---

### Post by Ek0nomik on 2007-08-18
You are using the Live CD I presume?

I haven't had this issue before myself, but I am led to believe that one of your partitions is being automatically mounted by Ubuntu and thus GParted won't let you use it.

If you go to Accessories/Terminal, and type:

```
sudo umount /dev/sda
```

Then try opening the Gnome Partition Editor.

If you run into more troubles, respond in this thread.

---

### Post by ccclairee on 2007-08-18
I haven't installed Ubuntu yet, I'm pre partitioning. I'm using a Gparted LiveCD,the Ubuntu Live CD wouldnt scan the devices, just freeze up.

When I look under hardware in windows, two drives are listed. Do I have two hardrives and just not know it?

---

### Post by Ek0nomik on 2007-08-18
I think you are the best judge as to how many hard disks you have in your box.  ;)

Did you use a partition editor in Windows to split up your hard drive into two partitions?  If not, then I would say you probably have two hard disks given that Windows wouldn't split your hard disk into two partitions automatically.

---

### Post by carloslosgrande on 2007-08-18
[FONT="Comic Sans MS"]Hi. My knowledge is very limited,... but this is my understanding; there are 2 main types of HDD - IDE which usually gets a device name like /hda or /hdb etc and the other is ATA (SATA) which usually gets a name like /sda /sdb etc.
I have 2 HDD, both SATA so they're called, first ;   /dev/sda   and the main partition on it is called, /dev/sda1
and, second ;   /dev/sdb and partition, /dev/sdb1
It looks like you've got 2 HDD one being an IDE and one ATA
[COLOR="DarkSlateBlue"]BUT I'm guessing[/COLOR].[/FONT]
[FONT="Comic Sans MS"]Can you have a look in the box?[/FONT]

---

### Post by louieb on 2007-08-18
> **ccclairee said:**
> One called dev/hdb1 and one called dev/sda. What are devices? 
The /dev/hda part refers to a hard drive. The 1 at the end refers to the first partition. If there was a 2nd partition it would be referred to as   /dev/hda2. 

The /dev/sda refers to a drive if that all there is then it has no partitions.  Kinda   strange. Heres a link that might help you. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by ccclairee on 2007-08-18
I opened the box, two seperate HDD.

Installed linux on one HDD, Windows on the other. Problem solved.

---

