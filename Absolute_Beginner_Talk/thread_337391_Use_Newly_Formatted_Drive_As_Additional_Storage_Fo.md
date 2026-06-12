---
title: "Use Newly Formatted Drive As Additional Storage For Programs"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-12
Hey All!

You may have seen my recent post on how I wanted to change my Simple Tech 200 gig hard drive USB to a useable harddrive in Ubuntu. Now that I've crossed that bridge, it's time to cross another :)

I would like to use the space on my new harddrive to install more programs to my Ubuntu installation which is on my 50 gig internal harddrive....

Not sure how to go about it, although it isnt really needed.... Just something I was wondering about.....

My setup is a 60 gig windows partition and a 60 ubuntu dual boot, with the Simple Tech formatted in FAT32 for extra file and such....

---

### Post by Shatrat on 2007-01-12
I'm not totally sure what your setup is.  I think you have 2 hard drives, one 200gig fat32 and one 120 that is half windows and half ubuntu / partition?

First of all, I recommend you format the 200 gig drive as something other than fat32.  Fat32 has lots of shortcomings such as not being able to store files over 4 gigabytes.  If you format it as Ext3 you can still read it in windows using the fs-driver from fs-driver.org

If you have 50-60 gigs for your / partition you really dont need more space for installing programs unless you like to install lots and lots of really large ones like games.  Also, is the 200gig drive still in the USB enclosure? I dont see any good reason to install things onto a removable device.

---

### Post by Fingerz91 on 2007-01-13
> **Shatrat said:**
> I'm not totally sure what your setup is.  I think you have 2 hard drives, one 200gig fat32 and one 120 that is half windows and half ubuntu / partition?

First of all, I recommend you format the 200 gig drive as something other than fat32.  Fat32 has lots of shortcomings such as not being able to store files over 4 gigabytes.  If you format it as Ext3 you can still read it in windows using the fs-driver from fs-driver.org

If you have 50-60 gigs for your / partition you really dont need more space for installing programs unless you like to install lots and lots of really large ones like games.  Also, is the 200gig drive still in the USB enclosure? I dont see any good reason to install things onto a removable device.

You're completely right as to my setup... One internal hard drive 120gig that is half windows and half ubuntu. The 200 is just a USB external that I was wondering if I cold use to add more programs onto... just out of curiosity I guess :)

It really isnt all that earth shattering.... If you guys think it best, I'll just leave the 200 alone and use my pc regularly.

---

