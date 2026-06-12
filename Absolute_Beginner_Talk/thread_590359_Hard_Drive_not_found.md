---
title: "Hard Drive not found"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Otisgoad on 2007-10-24
well this is my problem:
I have six hard drives and ubuntu 7.10 (run from CD) sees every one but the one i want to install it on... i have Win XP installed and it sees it just fine. it is formated NFTS and works fine in XP. i am VERY new to Linix but willing to climb over the learning curve. having read other similar posts i used the command "sudo lshw | less" and this is the output for the scsi device i am using for the drive in question:

 *-scsi
                description: SCSI storage controller
                product: AIC-7892B U160/m
                vendor: Adaptec
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: scsi4
                version: 02
                width: 64 bits
                clock: 66MHz
                capabilities: scsi pm bus_master cap_list scsi-host
                configuration: driver=aic7xxx latency=64 maxlatency=25 mingnt=40 module=aic7xxx
              *-disk
                   description: SCSI Disk
                   product: ATLAS10K3_18_WLS
                   vendor: QUANTUM
                   physical id: 0.1.0
                   bus info: scsi@4:0.1.0
                   logical name: /dev/sde
                   version: 020K
                   serial: 342124551905
                   size: 17GB
                   capacity: 17GB
                   capabilities: 10000rpm partitioned partitioned:dos
                   configuration: ansiversion=3
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: scsi@4:0.1.0,1
                      logical name: /dev/sde1
                      capacity: 17GB
                      capabilities: primary bootable


the drive listed is the one that windows is on but the one i want to use is not there. it is the same brand and similar model but a 9 gig. 
the rest of the drives are listed too but i didnt think it was important. please help. Thanks!
Otis

---

### Post by Pumalite on 2007-10-24
Make sure is recognized by BIOS first.
(and make sure is formatted)

---

### Post by Otisgoad on 2007-10-24
Both the motherboard BIOS and the SCSI card BIOS recognize it and it is formated NFTS.

---

