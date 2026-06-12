---
title: "[PPC] Best Way to Transfer Files from iBook to Linux"
date: 2013-12-29
forum: Apple Hardware Users
---

### Post by cool3 on 2013-12-29
I'd like to install Lubuntu on my iBook but I've had a hard time pulling files from it.  I've tried to use Gparted to partition an external HD in Fat32 to drag-and-drop but with a lot of files it does not work.  For some reasons Gparted will not allow me to make a partition in HFS.  I'd burn the files onto discs but I can't seem to get the optical drive to burn.   

I noticed people recommend SuperDuper and Carbon Copy but that for making a complete backup.  All I want to do is take my core files from this iBook and move it to my main laptop which runs Linux Mint.  There's no point in a dual-boot considering the age of this Mac and it only has a 40gb harddrive. 

So what's the best way to transfer files from a PPC Mac to a Linux machine?

---

### Post by dand1972 on 2013-12-30
Network the computers?  Assuming your iBook has OS X, enable Remote Login in System Preferences --> Sharing and then use gFTP or a similar application on your Mint laptop to transfer the files.

---

### Post by cool3 on 2013-12-30
I tried to transfer the files using "scp -r" command in the Mac terminal.  However I am getting this error

> ssh: connect to host *IP Adresss *port 22:Operation timed out lost connection'

Terminal version 1.4.6

---

### Post by raphael-platte on 2014-01-01
> **cool3 said:**
> There's no point in a dual-boot considering the age of this Mac and it only has a 40gb harddrive.

Well, it's a lot of fun... And works well.

Just my $2/100

---

### Post by cool3 on 2014-01-01
I was able to partition an external HD after reaizing I needed to download the hfs formatting software for Gparted.  I was able to transfer files onto a partitioned hfs+ part of the external HD once I formatted it. 

@rachel-platte - I like Macs but at this point it seems Linux is the best option for the iBook considering I don't want to have to buy a install disk for a later Mac OS which would be outdated and unsupported at this point anyway.  

I made a disk image using the disk utility in case I don't like my forray into Linux on a PPC Mac.

---

### Post by raphael-platte on 2014-01-01
> **cool3 said:**
> I was able to partition an external HD after reaizing I needed to download the hfs formatting software for Gparted.  I was able to transfer files onto a partitioned hfs+ part of the external HD once I formatted it. 

@rachel-platte - I like Macs but at this point it seems Linux is the best option for the iBook considering I don't want to have to buy a install disk for a later Mac OS which would be outdated and unsupported at this point anyway.  

I made a disk image using the disk utility in case I don't like my forray into Linux on a PPC Mac.

I thought you were going to keep OS X on it. My bad.

---

### Post by cool3 on 2014-01-01
The Max OS X installation is so bloated I only have 7gb, not much space for a dual boot.

---

### Post by raphael-platte on 2014-01-01
> **cool3 said:**
> The Max OS X installation is so bloated I only have 7gb, not much space for a dual boot.

Big thumb drive?

---

