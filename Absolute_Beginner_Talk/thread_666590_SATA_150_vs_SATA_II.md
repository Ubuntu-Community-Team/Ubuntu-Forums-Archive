---
title: "SATA 150 vs SATA II"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by darthlunchbox42 on 2008-01-13
I wasn't sure where to post this, so I decided to put it here, seeing as though it describes my relationship with any Linux system perfectly.  

Right now, I am running on Windows XP, but I want to set my computer to dual boot with Ubuntu.  I tried to do this a few months ago, however Windows would not boot and I could only run on Ubuntu (not a bad thing, just fairly frustrating).  I had them both booting off of a 250GB SATA150 drive that I had partitioned.  After a while, I just reinstalled Windows and eliminated the Ubuntu partitions.  This time I am going to attempted it on two hard drives.  I'm going to boot Windows off the SATA drive that I am currently using, and I plan on buying another SATA on which I will put Ubuntu.  The problem arises in the fact that I've been out of game, so to speak, for a long time.  I discovered SATA II, and did some looking and found all the info about it, except for one thing:  I don't know if I can put in a SATA II HD, and have it be compatible with my computer.  I've read some places that one needs a jumper of some sort to make it compatible.  But, I can't find a HD that says it comes with one of these jumper thingies (I've been perusing newegg.).

I want to know if SATA II HDs come with this fabled jumper, and if they do, can I plug them in normally?

---

### Post by kyphi on 2008-01-13
There is no jumper.  Just install your hard drives and connect them to your SATA ports.

I have two SATA II hard drives with Ubuntu on one and XP on the other.

---

### Post by logos34 on 2008-01-13
> **kyphi said:**
> There is no jumper.  Just install your hard drives and connect them to your SATA ports.

I have two SATA II hard drives with Ubuntu on one and XP on the other.

Just curious, what make of drives do you have?  No jumper for backward compatibility with sata150-only boards/controllers?  (I thought only Hitachi didn't have jumpers, instead using firmware settings).

---

### Post by blueridgedog on 2008-01-13
From my exp. most SATAII drives fall back to SATA150 w/out any issue, most also come with a jumper to force SATA150.  I have an SATA150 MB and am using SATAII drives at the moment w/out the jumper.

---

### Post by kyphi on 2008-01-13
darthlunchbox42 - you forgot to mention which motherboard you have.  That would indicate which SATA controller is installed.

Do you intend to run RAID?



logos34 - Seagate SATA II HDDs - MoBo controller hub = ICH8R/ICH8DH

---

### Post by darthlunchbox42 on 2008-01-16
kyphi, I've got a Gigabyte GA-K8NS Rev. 2.0 mobo.  I finally got a look-see through the manual for it, and it supports SATA 150, but I don't think it mentions SATA II.  Sorry for the late reply, classes decided that my profs decided that they all wanted to kill me with homework. :-x

---

### Post by kyphi on 2008-01-16
All I can see in your MoBo manual is that it supports two SATA drives.

If you are unsure, get another SATA-150 drive.  I believe that you can still buy those.  If your controller only supports SATA-150 then the installation of a SATA II drive would not give you anything faster..

---

### Post by blueridgedog on 2008-01-17
I doubt it would give him anything faster, but I recommend buying SATA II for the future,as most drives are backwards compatible.

---

