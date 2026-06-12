---
title: "Preinstallation questions"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-05
I have tried ubuntu 6 in a virtual environment once. I have decided to take another step and do dual boot.

I have partition magic on windows, I have created it so that theres 25ish gigs free

[IMG]http://img413.imageshack.us/img413/2107/drivexo3.jpg[/IMG]

Now for my questions:

Is this enough space?

They say that swap should be 2x RAM, I have 2 Gigs RAM but it doesn't allow me to create more then 2 gigs of swap space.

After I set this partition active, do I have to use the grub dual boot or can I use the windows boot loader, If i can use the windows one, how do I do it?

I have Intel wireless and gfx cards. Can I install beryl on it? Can I go on the internet with it?

And finally Notice the 2 extra partitions, I use them as partial storage and partial back up partitions, should I make it FAT32 so Linux can access them?

Thats all for now, thanks for answering.

---

### Post by Pumalite on 2007-10-05
You will have more than enough with 500 MB of /swap. You can access windows ntfs from Ubuntu installing ntfs-3g, no problem.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
(you can install Beryl and go on the Internet, and MUCH MORE)

---

### Post by perce on 2007-10-05
If you want to suspend to disk (hibernate) you need at least as much swap as ram.

---

### Post by InsertNameHere on 2007-10-05
OK, So if I don't want Grub on the MBR because if something goes wrong I can't fix it. How do I make ubuntu in the Windows boot loader screen? Because after installation the ubuntu partition should be set to active, but if there's nothing in the MBR then does that mean i'll get a message saying no OS present?

Also do I have to install extra drivers for internet and gfx or is it all out of the box?

---

### Post by benerivo on 2007-10-05
You will need to use grub rather than the windows boot loader if you want Ubuntu. There should be no problems, and you should get the option to boot in to either Ubuntu or windows.

The gfx is out of the box.
What internet set do do you have? Broadband, Router, Ethernet, USB, etc...

Backup all important files from windows before you install.

---

### Post by InsertNameHere on 2007-10-05
It's a intel card, connected to a wireless router.

---

### Post by benerivo on 2007-10-05
Then i'm not sure it will be 'out of the box' for the internet. Is it [one of these]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")

---

### Post by bodhi.zazen on 2007-10-05
> **InsertNameHere said:**
> I have tried ubuntu 6 in a virtual environment once. I have decided to take another step and do dual boot.

I have partition magic on windows, I have created it so that theres 25ish gigs free

Now for my questions:

Is this enough space?

They say that swap should be 2x RAM, I have 2 Gigs RAM but it doesn't allow me to create more then 2 gigs of swap space.

You need ram X 2 , max 1 Gb of swap. You need swap = ram for suspend on laptops.

> After I set this partition active, do I have to use the grub dual boot or can I use the windows boot loader, If i can use the windows one, how do I do it?

You need to set one partition as "boot". The linux partition does not need to be marked as bootable.

Last, I advise you partition with the partitioner on the Ubuntu CD, gparted. partition magic usually, but not always works well with linux.

---

### Post by Duck2006 on 2007-10-05
May be this will help in booting linux without writing to the MBR

[http://www.softpanorama.org/Unixification/dual_boot.shtml](http://www.softpanorama.org/Unixification/dual_boot.shtml)

---

### Post by InsertNameHere on 2007-10-05
OK, as I am posting this ubuntu is installing (yes im on a live CD).

The GFX and internet worked fine, And I really don't see the point anymore for using the windows boot loader. 

I had 1 problem on the live CD :

My sound is coming out BUT it's VERY VERY quiet, I cranked everything up to the highest and it's still quiet.

Also

The automatic guided partitioner failed somehow so i had to partition manually.

---

