---
title: "RAID Drives.. anyone an expert..."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by bigun on 2007-02-03
****Hi Everyone, 

I have a Dell Poweredge 2300, PII 350Mhz, 256Mb Ram, 6 SCSI 9Gb disks set up as 3 logical 9Gb Drives.  

I can't install Ubuntu from boot, as the partitioner can't recognise the disks.

Running the Live CD of 6.06 allowed me to install and automatically repartitionaing the HDD's, However, the machine won't reboot and when I try to use to Live CD again I get a huge list of logical drive errors, then it boots into the "desktop".  

I could use some help checking what is going on... Thanks.

---

### Post by chach man on 2007-02-03
Im not a math major but how do you have "6 SCSI 9Gb disks set up as 3 logical 9Gb Drives" or am i missing something do you intend on having extra unallocated space?

have you ever had it setup like you want or is this a first time try.

---

### Post by danielph on 2007-02-03
It sounds like the RAID isn't configured correctly. Do you have RAID setup disks with the Dell.

I guess you are using RAID 1 (mirror) as half of your space being used?

Saw this link, it may help
[http://williamtasso.com/tech/poweredge2300.html](http://williamtasso.com/tech/poweredge2300.html)

---

### Post by bigun on 2007-02-03
Thanks for the replies. 

I have 6 physical SCSI disks, they are setup as RAID1, Mirrored, which means logically they appear to Ubuntu as sda, sdb, sdc, - 3 disks.  

It was an NT4 machine, all working fine.  I tried to install edgy... disks couldn't be recognised.

Went to 6.06, Live CD, ran fine, found the disks, MegaRAID, I installed. 
Rebooted and it hung. 
Rebooted and it told me logical disks not loaded. 
Put in the Live CD again and it took ages to boot and then gave me loads of logical disk errors. 

I don't have to setup disks, will go and look on dells website. 

I did repartition the disks, but the RAID controler is hardware and should handle me moving partitions.  Mmmmm... some more coffee methinks...

---

### Post by danielph on 2007-02-03
The upshot of the link I gave you, the guy had seen this problem with Linux on other Dell's and he plugged the disk straight into the spare adaptec channel reconfigured and it worked. Looks like there was some problem with the Perc controller and Linux...

If you are running a Perc controller in this box you may want to google a bit for supported kernels and running it with Linux.

---

### Post by bigun on 2007-02-03
Woohoo... totally correct.. the NVRAM was incorrectly configured.  

Re-configured the RAID controller and all is now working... I did find this artical which is exactly the problem I went through with edgy... maybe it will help someone else...

[http://williamtasso.com/tech/poweredge2300.html](http://williamtasso.com/tech/poweredge2300.html)

Thanks for the input guys.

---

### Post by randyleepublic on 2007-02-06
I use a dell perc (adaptec) hardware scsi raid card.  I have 6 drives confured as raid 10, (three mirror sets striped).  I am constantly having coruption entering my ext3 file systems.  Before I got the dell card, I was using an LSI Logic card.  Same difference.  When I run Windows with these cards/drives/raid configuration, no issues.  Thanks god ext3 is robust enough to recover every time, but this sure gets old.  Clearly the drivers for ubuntu are defective.  I am running dapper - the drivers are automatically installed. Does anybody have any idea how to get better drivers?

---

### Post by danielph on 2007-02-06
This talks about installing from a perc raid install disk for Ubuntu and Debian. A bit of googling would find the iso I would think.
[http://mcwhirter.com.au/craige/blog/2006/Using-a-Standard-Debian-Ubuntu-Kernel-on-DELL-PERCraid-Servers](http://mcwhirter.com.au/craige/blog/2006/Using-a-Standard-Debian-Ubuntu-Kernel-on-DELL-PERCraid-Servers)

If that doesn't work there are some old links for other distros. Alternative is to perhaps look at using another distro.

[http://linux.dell.com/storage.shtml](http://linux.dell.com/storage.shtml) - aacraid and megaraid
[http://linuxmafia.com/faq/Hardware/perc.html](http://linuxmafia.com/faq/Hardware/perc.html) - list of controllers and drivers (very old post)

---

### Post by bigun on 2007-02-08
Hi guys... after getting it working, my NVRAM configuration is inconsistent with my drive configuration.... ahhh.. 

However, I found this [http://linux.dell.com/storage.shtml#megaraid_scsi]("http://linux.dell.com/storage.shtml#megaraid_scsi") It has a huge list of untils and firmware...

Anyway, there is known issues with RAID PERC older than firmware v 3.13, which could explain my problems.  I will try to update an let you know how I get on. 

Best.

---

### Post by bigun on 2007-02-08
Wonderful... 

I updated the BIOS for the PERC (megaRAID) card, the System Bios and with some jiggery pokery, a copy of a win98se (ah, I know) boot floppy, and an update for the embedded server management and system backplane bios.....  I have managed to get my PE 2300 up and running. 

It's booting every time.  

Boy, that feels great.  Don't you just love it when a plan comes together.. wait... what plan?

Adios.

---

### Post by kinohead on 2007-02-11
OK, I am glad I found this thread, as I was about to jump out a window... (may do it anyway, but... that's for another day)

I have a Dell Power Edge 1300/500 (dual 500 pentium processor) with a gig of ram and 5 x 9.1 gig drives set up in a RAID 5 configuration.

Picked it up a local Goodwill for $20 as nobody knew what it was (Won't play Half LIfe, dude!) and I wanted to get into messing about with a LAMP server on Dynamic DNS.

I have Ubuntu 6.06 on my laptop (HP DV8000) so I wanted to keep the same distro on this to minimize my brain flux.  Been dabbling in Linux for years, but haven't made much headway, so elimination of variables is toward "goodness".

The MB system bios is version A07, the Adaptec ACI-7890 is V2.01 Dell 01 and the PERC2/SC bios is 2.50 with 16 MB DRAM on the card.

Please confirm;  if i boot with a Windows 95 or 98 startup disk, I should be able to run the bios and firmware updates via floppy disk swapping and then load 6.06 LAMP?

Should I just go to Fedora Core 6 and try that or am I going to hit the same brick wall?

Thanks!

PS:  I am guessing that if I went the route of removing the PERC2 card and plugging the SCSI cable into the ADAPTEC ACI-7890, the box would take a big performance hit when you have to run the RAID in software;  correct?  Would it be an issue?

---

