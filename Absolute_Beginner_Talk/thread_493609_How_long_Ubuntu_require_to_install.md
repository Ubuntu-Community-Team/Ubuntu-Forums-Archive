---
title: "How long Ubuntu require to install"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by prabhaMV on 2007-07-05
Hi all,

I am new to Linux and trying to load Ubuntu 7.04 on my Laptop

Mine is dual boot system with Windows XP already installed.

Now trying to install Ubuntu from 1hr its  going on and on....

My system configuartion:-

80GB hard disk,1GB RAM,2.2 GHz

After loading Live CD, I selected "START OR INSTALL UBUNTU"

Please any one can help me....!!!

---

### Post by Krosis on 2007-07-05
Is it making any slow progression or is it just stuck?

---

### Post by the.phantom on 2007-07-05
stuck !in the frist screen with the live cd one of the options is to check the cd, might try that
sorry i am a lightweight 

but that is too long for just a desktop install
now you said yours is a dual boot
did you use the live cd to do it?
and what is the size of the U partition for ex3,  and such?

---

### Post by Krosis on 2007-07-05
Read this guide, and I suggest paying special attention to the MD5 Sums section.  This is where I was thrown off when I first started out.  Went through about 3 CD's before I simply read the manual.  That was all I needed to do.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Good luck.

---

### Post by prabhaMV on 2007-07-05
Actually I am not able to make out ...from past 1 hr I am seeing the same screen ( no progress bar to make out )

In the link below...
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Vista & Ubuntu - Install Ubuntu --> Image name below INSTALL UBUNTU

---

### Post by xtrm_redbull on 2007-07-05
You need to check the cd for errors its included in the live cd menu. But I suggest you should do some reading first. Heres the link [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) . Everything you need to about downloading to installing ubuntu is there, plus more info. Good luck :p

---

### Post by Krosis on 2007-07-05
I'm not sure how much I can help you.  I'm not dual booting.  But it sounds to me like a CD defect.

---

### Post by lisati on 2007-07-05
When I first tried to install Ubuntu on my laptop from a live CD, it didn't seem to do much other than get my CD-rom working overdrive, yet the same CD worked in my desktop. I finally had success using the "alternate" CD. Perhaps this will an option for others who have trouble with the Live CD appearing to get "stuck"

EDIT: I read on another thread that the Live CD uses a "swap" partition if its available. When I've been doing a "clean" install, this seems to "un stick" the Live CD

---

### Post by TheTux on 2007-07-05
> **prabhaMV said:**
> Hi all,

I am new to Linux and trying to load Ubuntu 7.04 on my Laptop

Mine is dual boot system with Windows XP already installed.

Now trying to install Ubuntu from 1hr its  going on and on....

My system configuartion:-

80GB hard disk,1GB RAM,2.2 GHz

After loading Live CD, I selected "START OR INSTALL UBUNTU"

Please any one can help me....!!!

with your system configuration it should take about 25-30 minutes to install

---

### Post by prabhaMV on 2007-07-06
Hi all,

Thanx for the help..It was problem with iso file as MD5Sum mismatched...

I am almost at finishing stage...want some clarifiaction...

Its asking as below please let me know which one to select:-

PREPARE DISK SPACE...

How do u want to partition the disk

1. Guided - resize SCSI1 (0,0,0),partition #1(sda) and use freed space
            New partition size 79% ( 44.9GB)

2. Guided - use entire disk.
           SCSI1(0,0,0) (sda) -80.0 GB ATA FUJITSU MHV2080B

3. Manual

-----------------------

By default option (1) got selected.

As I have already done partition using partition magic ( windows - 60GB, Ext2 - 10GB and swap 5GB)

Please let me know which one to choose..

I tried selecting option 1 but it says provide partition for Root "/"

Waiting for ur response...

Thanks 
prabha

---

### Post by kpkeerthi on 2007-07-06
Choose manual and select the appropriate mount points for root / and swap

---

### Post by Old Pink on 2007-07-06
Make a note of the label of the partition you want Ubuntu on (hd**) and set the mountpoint as "/" :) 

You shouldn't need 5GB for Swap, I'd go 14.5GB for Ubuntu and 512Mb for swap. :D 

With 1GB of RAM, you'll hardly ever need swap. :)

---

### Post by prabhaMV on 2007-07-06
Hi all,

I am in between installation...want some clarifiaction...

Its asking as below please let me know which one to select:-

PREPARE DISK SPACE...

How do u want to partition the disk

1. Guided - resize SCSI1 (0,0,0),partition #1(sda) and use freed space
New partition size 79% ( 44.9GB)

2. Guided - use entire disk.
SCSI1(0,0,0) (sda) -80.0 GB ATA FUJITSU MHV2080B

3. Manual

-----------------------

By default option (1) got selected.

As I have already done partition using partition magic ( windows - 60GB, Ext2 - 10GB and swap 5GB)

Please let me know which one to choose..

I tried selecting option 1 but it says provide partition for Root "/"

Waiting for ur response...

Thanks 
prabha

---

### Post by Old Pink on 2007-07-06
Don't double post. ;) 

Choose option 3.

Set the 10GB ext2 mountpoint as / (for root) :) 

I also recommend, before doing this, shrinking your 5GB swap down to 1GB or 512Mb, and making your Ubuntu partition larger. Swap is only really used once your RAM is full, and with Ubuntu and 1GB you'll hardly ever fill 1GB of RAM, definitely not 6GB. ;)

---

### Post by prabhaMV on 2007-07-06
If I am doing it manually and after selecting /dev/sda5 ext2 /media/sda5 for root / 

Then it pop up " NO ROOT FILE SYSTEM" ..please correct this from partition Menu.

---

