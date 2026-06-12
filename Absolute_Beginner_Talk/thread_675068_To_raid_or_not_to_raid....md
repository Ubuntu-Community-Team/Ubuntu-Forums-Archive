---
title: "To raid or not to raid..."
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-01-22
I'm in a dilemma here.. I'm fairly new to Linux and I have always had the impression that a Stripe 0 Raid was good to have in regards to performance.  I've been scanning through all the posts and whatnot to come to realize that my The Silicon Image 3132 controller is not a true raid at all (in terms of software vs hardware)? :(

:?:  If I'm wrong please educate me so I can get a full understanding of this already.

With that in mind; is there any benefits to me setting up a "FakeRaid" besides the fact that my two drives will appear as one?  I've been holding off all my WINE installations and a major part of my downloading because I want to move my home folder to these 2 drives along with any storage.

Anyways... any input/suggestions would be greatly appreciated  #-o


This is the related hardware if it helps at all...
[LIST]
[*]Motherboard - [[COLOR="Blue"]ASUS Striker Extreme[/COLOR] ]("http://www.asus.com/products.aspx?modelmenu=1&model=1439&l1=3&l2=11&l3=397")
[*]Primary Disk (Dual Boot) - [[COLOR="Blue"]Western Digital Raptor X WD1500AHFD 150GB[/COLOR]]("http://www.newegg.com/Product/Product.asp?Item=N82E16822136011")
[*]Secondary Disks (I have two of these) - [[COLOR="Blue"]Western Digital Caviar SE16 WD7500AAKS[/COLOR]]("http://www.newegg.com/Product/Product.asp?Item=N82E16822136131")
[/LIST]

---

### Post by Foxray on 2008-01-22
A little info; Software raid is not really fakeraid its more like software controlled vs hardware controlled. Software raid has its advantages over hardware raid and vice versa. Here are some Advantages and Disadvantages:

Software Raid Advantages:
-Cheap cost effective solution
-easy to implement

Software Raid Disadvantages:
-Only limited to raid levels 0,1 and 5
-No hot swapping

Hardware Raid Advantages:
-Have the ability to choose any raid level you want
-hot swapping available

Hardware Raid Disadvantages:
-Expensive
-can be hard to implement

Note that when you implement a Raid0, yes you will have an increase in performance but remember that in Raid0 if one of your drives fail, you will lose all your data (unless its a Raid5). instead of having sda1 sda2 etc. you will have a single drive that is named like md0.

---

### Post by insane_alien on 2008-01-22
RAID 1 will also give you a performance boost AND data security, though this is at the cost of one disk worth of storage.

---

### Post by Aysah on 2008-01-22
> **insane_alien said:**
> RAID 1 will also give you a performance boost AND data security, though this is at the cost of one disk worth of storage.

now I've used RAID 0 before but never RAID 1....  How does RAID 1 give added security?

---

### Post by Aysah on 2008-01-22
> **Foxray said:**
> A little info; Software raid is not really fakeraid its more like software controlled vs hardware controlled. Software raid has its advantages over hardware raid and vice versa. Here are some Advantages and Disadvantages:

Software Raid Advantages:
-Cheap cost effective solution
-easy to implement

Software Raid Disadvantages:
-Only limited to raid levels 0,1 and 5
-No hot swapping

Hardware Raid Advantages:
-Have the ability to choose any raid level you want
-hot swapping available

Hardware Raid Disadvantages:
-Expensive
-can be hard to implement

Note that when you implement a Raid0, yes you will have an increase in performance but remember that in Raid0 if one of your drives fail, you will lose all your data (unless its a Raid5). instead of having sda1 sda2 etc. you will have a single drive that is named like md0.

thanks, that was very informative... I definitely want to do a raid but up to this point have only done it through the BIOS.  Apparently from what I have read, the guides say to turn off the raid in the BIOS.  -shrugs-  Now the part where I'm totally lost at... :(

Which way is the easiest and smartest way to go about implementing this raid?  I see some people suggesting actually building a custom kernel (shutters at thought), and then even others suggesting either MDADM or DMRAID.

---

