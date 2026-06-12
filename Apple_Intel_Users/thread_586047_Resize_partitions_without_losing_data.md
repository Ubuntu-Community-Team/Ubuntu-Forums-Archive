---
title: "Resize partitions without losing data?"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by dmber on 2007-10-21
So, when I set up my Macbook to dualboot OS X and Ubuntu I figured OS X would be my main OS.  That has changed.  I have a 60 gig HDD and right now it's something like 45 gigs for OS X and 15 for Ubuntu.  I want to switch that, without messing up any of the data on either partition.  Worst case scenario would be to cut 30 gigs from the OS X partition and just make that a "storage" partition that both OS X and Ubuntu can write to.  Can I shrink my OS X partition without losing my data?

How would I go about this?

---

### Post by alephsmith on 2007-10-22
diskutil resizeVolume should be able to non-destructively resize your OSX partition.

---

### Post by dmber on 2007-10-22
do i boot off of my system disk or can i do that if i'm booted into OS X?  or is that an Ubuntu command?

---

### Post by cyberdork33 on 2007-10-22
> **dmber said:**
> do i boot off of my system disk or can i do that if i'm booted into OS X?  or is that an Ubuntu command?
It is an OSX command. It is the command that the Bootcamp utility is a GUI for. I am not sure if you can run it on your running partition or not. It has been a long time since I used it myself.

You can also try Gparted. It can shrink HFS+.

---

### Post by wigglydiggly on 2007-10-23
I'm kind of in the same boat.  I already shrunk osx down to 24 gigs.  Ubuntu is currently at 20 gigs and I have 30 gigs free.  I want to increase my linux partition, I also need to increase my /swap from 500mb to 1.5gigs so I can enable Hibernate.  I have not been able to resize my linux partition using a live cd.  Any ideas?  Macbook C2D sec gen.

---

### Post by alephsmith on 2007-10-23
Resizing your swap can be desructive so you my like to try from within OSX to resize using diskutil resizeVolume which supports "Swap" as a filetype.

It also supports "Linux" but I do not now what filesystem that is or if it is non-destructive.

---

