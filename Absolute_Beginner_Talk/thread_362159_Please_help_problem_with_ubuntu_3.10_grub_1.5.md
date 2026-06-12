---
title: "Please help problem with ubuntu 3.10 grub 1.5"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by magnox on 2007-02-15
Hi there,
I am new to this forum as I have been looking for some help if anyone would be so kind to be able to help me.  I will try to explain the situation but please forgive me if I do not use all the correct terminology as I have never had any dealings with ubuntu before.

I recieved a PC I bought today that has been running ubuntu 3.10 grub 1.5 from the previous owner.  When booting up the pc it loaded a list of commands as though it was initialising itself and it came up with the ubuntu 3.10 logon grub 1.5.  I of course cant access the old account as it is passworded but I wanted to use windows 98 se not ubuntu so I restarted the computer and booted from the windows 98 se cd.

It loaded up the windows 98 se screen and said it would have to remove some old files from the computer before installing, I clicked continue and it just went to the next screen and would progress no further.

I restarted again to make sure it wasnt the hard drive that was dead without the windows cd and it once again loaded all ubuntus files and came to the ubuntu logon, so I restarted the computer and used fdisk to try to look at the partition to remove it so I could install windows, I tried with both the hard disk support enabled and also disabled, trying to look at any of the options on the screen in fdisk whether it be removing partition or viewing just resulted in it locking up.

I then tried to look in the google search engine (on my old macintosh computer) on removing ubuntu to try to install windows and it suggested that the mbr would be pointing to ubuntu so I would need to type the command in the prompt after starting the computer without cd support: fdisk /mbr .  I did this and restarted and tried to boot from hard drive and it comes up with something like no operating system installed.

I restarted again thinking I would now be able to change the partitions so I could install windows and once again it just locks after selecting any option to view or change the hard drive partitions in fdisk.  I tried the windows 98 se install again too and again it locked at the same point.

Please if anyone can help me with this problem  or has any suggestions on what I can do to get the hard drive in  a position to install windows 98 se I would be very grateful, I know nothing about ubuntu other than its based on linux technology and I am very thankful if anyone could give me hep with this please.  Thankyou for your time.

---

### Post by wieman01 on 2007-02-15
Get yourself the latest Ubuntu Live CD, boot from CD, fire up Gnome Partition Editor and format your entire harddisk. That's the easiest solution I can offer. Hope you know how to use a partitioning tool...

---

### Post by jvc26 on 2007-02-15
I'd follow the instructions here: (Up to the partitioning scetion if you dont want to install the OS)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Or I'd get the GParted livecd and use that to wipe the drive:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
You could try just installing the new Ubuntu and giving that a whirl though ;)
Il

---

### Post by magnox on 2007-02-15
thanks for your help all :) I am downloading ubuntu live cd now and will try and burn it on my macintosh if I can find the software :) Thanks once again, i'll let you know how it goes.  And i'll have a look at ubuntu while i'm at it!

---

