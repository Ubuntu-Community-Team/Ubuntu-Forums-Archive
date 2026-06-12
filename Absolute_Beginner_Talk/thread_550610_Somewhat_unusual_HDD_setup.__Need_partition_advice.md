---
title: "Somewhat unusual HDD setup.  Need partition advice"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Lawngnome on 2007-09-14
I'm running an amd athlon64 3500+ with 2gb of ram.  I have 2 hard drives the first is a 69gb 10,000 rpm sata drive.  The second is 320gb 7200 rpm sata drive.  

I want to dual boot linux and winXP using the 10k rpm drive as a system drive and the 7200 rpm drive for data.  I want both os's and programs to install on the system drive since it is faster, and use the data for all my document storage etc.  But I want the data drive to be fully accessible by both os's.

So I'm not sure what would be the best way to set up my partitions to keep everything neat and orderly.

---

### Post by hyper_ch on 2007-09-14
Ok, the 69gb drive needs to be sata1

The partition it the following:

(1) primary partition for windows - I'd say about 30gb

(2) primary partition - SWAP partition, at least 2GB if you want to use hibernate...

(3) primary partition - Ext3 - mounted as root "/" - about 20 GB

(4) primary partition - Ext3 - mounted as "/home" - the rest

320GB drive

(1) primary partiton - Ext3 - mounted as /home/USER/data or /home/USER/Desktop/data (wherever you want it) - 320 GB

in Windows you can install the Ext2/3 drivers to gain read/write access to the linux partitions.

I don't think Fat32 is an option as there is file limits of 4GB....

and also I would not make it ntfs

---

### Post by splintercellguy on 2007-09-14
Is it possible to put /home on an NTFS partition? If that's the case, why not just split the OS partitions on the 69 GB and put all the data on 320 GB?

---

### Post by Lawngnome on 2007-09-14
When I install a program or plugin etc in linux is it installed in the / partition or would it be installed under the user in the /home partition?  I like the idea of making a 34gb ntfs for windows, and then a 2gb swap and 32gb / partition and then just use the entire 320gb for /home.

---

### Post by splintercellguy on 2007-09-14
The program/plugin would most likely be installed in the OS in directories on /, while settings for those apps/plugins would be stored somewhere in /home.

---

### Post by Lawngnome on 2007-09-14
Ok thanks I appreciate the help.

---

### Post by Lawngnome on 2007-09-14
Ok now I'm having a little trouble setting up the paritions manually in the install.  I have half of the 69gb drive set up for windows, the other half has a 4gb swap and 30ish gb / partition.  But when I try and create a partition on the 2nd drive I get this error "Can't have the end before the start".

---

