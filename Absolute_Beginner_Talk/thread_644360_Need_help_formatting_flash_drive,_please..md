---
title: "Need help formatting flash drive, please."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-18
Yesterday I made a Live CD for Gparted from information I got here:-   [http://tinyurl.com/rk4qp](http://tinyurl.com/rk4qp)

What I wanted was to be able to create an 850MB partition on a 4GB Flash Drive.  Unfortunately the largest partition that Gparted would allow me to make was 722MB.  I even tried it on a 2nd 4GB flash drive, with the same result.

Could it be that I am doing something wrong, or is it more likely that this would be a function of what brand of Flash Drive I use?

TIA

---

### Post by Nano Geek on 2007-12-18
It's probably caused by the filesystem type used.
Are you using FAT32?

---

### Post by LaRoza on 2007-12-18
What flash drive is it?

FAT32 should work, if you are not using it. Don't use FAT16.

---

### Post by L Campbell on 2007-12-19
> **LaRoza said:**
> What flash drive is it?

FAT32 should work, if you are not using it. Don't use FAT16.

I don't know the brand name of my 4GB Flash Drive but here is some info:-

 *-disk
             description: SCSI Disk
             product: USB Flash Drive
             vendor: USB 2.0
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             size: 4048MB
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sdb
                size: 4048MB
                capabilities: partitioned partitioned:dos
              *-volume:0
                   description: FAT16 partition
                   physical id: 1
                   logical name: /dev/sdb1
                   capacity: 721MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   logical name: /dev/sdb2
                   capacity: 3325MB
                   capabilities: primary

I have tried it with Fat 32, I have tried it with Fat 16 and I have tried another brand of 4GB Flash Drive but still cannot get it to make the partition larger than 722MB.

---

