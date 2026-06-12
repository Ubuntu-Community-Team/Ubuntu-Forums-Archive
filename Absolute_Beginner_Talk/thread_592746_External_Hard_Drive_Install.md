---
title: "External Hard Drive Install"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Vekin on 2007-10-26
Three Questions:

1.  Will I see a performance loss if I install ubuntu onto an external hard drive?
2.  Just how difficult would it be to do so in comparison to an internal hard drive install?
3.  What are some suitable, quick external hard drives that are 100 dollars, give or take?

Thanks!

---

### Post by KeaponLaffin on 2007-10-26
I can answer your 3rd question. I got a 60GB FireLite drive from CompUsa for about 75$ after taxes and I proly got ripped off ;)

As for the rest, I'm trying to figure it out too. Now with a real external drive (NOT a flash drive) you should be able to install it from the LiveCD just like you'd install it to a normal HD. My Ubuntu recognized the USB drive instantly and my BIOS allows me to boot off a USB so I think the LiveCD would pick it up too. But I haven't tried it.

Now off to look for the thread 'How to install Ubuntu to an external drive from Ubuntu w/o the LiveCD'
Good luck.

---

### Post by Yes on 2007-10-26
I got a 160 WD external hard drive for something around $100.  It was probably a bit more, but just look around on Newegg for the prices.  I haven't installed Ubuntu on an internal hard drive so I don't have anything to compare it to, but the install took about three hours or so, and it runs no slower than Windows (On the internal drive) does.

---

### Post by Vekin on 2007-10-26
I [found this]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/"), which may help some of you in the same position as me.  I haven't been able to test it out, as I've yet to purchase an external hard drive =/

---

### Post by louieb on 2007-10-26
Stuff to think about before installing on an external drive.

To dual boot you need a boot loader/manager.

The GRUB pointer can be installed in the MBR of your** internal drive**. If you do that then the external drive will have to be pugged in every time you start or reboot the PC. If it not plugged in the computer won't boot.

The Grub pointer can be installed in the MBR of the **external drive**.   If you that then you will have to create a boot CD or floppy.  OR  if the PC has the option you can go into your BIOS setup when you want to switch operating systems.  

I have 3 PCs set up to dual boot all installed on an internal drive. My external is used for data storage.

---

### Post by JasonBourneLinux on 2007-10-26
I installed 7.10 to external HD

1) Speed- not that big of a problem 
2) Booting- really convenient- my Grub is on external 

I have a 2 year old Maxtor -_- 200 GB HD in a Generic enclosure

tips- make sure you mess around with partition sizes (I got Error 18 from Grub 2 times)- backup your stuff and for me, cause I was paranoid, I disconnected all internal drives first 

best of wishes if you do decide to install on an external (its fun to try out Ubuntu and have something to use if msft windows goes down)

---

### Post by akiratheoni on 2007-10-26
I just got a Western Digital 500GB hard drive several weeks ago for $129. They're cheap these days :)

Oh I forgot to mention, the one that I got (My Book) will turn on and turn off with the computer as long as it's plugged in. So I think it makes everything a bit easier, especially if you install GRUB on the internal drive.

---

### Post by Specter043 on 2007-10-27
I picked this one up yesterday for $100.  It's a 320 GB mybook.  [http://www.circuitcity.com/ssm/Western-Digital-320GB-My-Book-Essential-Edition-2-0-External-Hard-Drive-WDH1U3200N/sem/rpsm/oid/193192/catOid/-12973/rpem/ccd/productDetail.do]("http://www.circuitcity.com/ssm/Western-Digital-320GB-My-Book-Essential-Edition-2-0-External-Hard-Drive-WDH1U3200N/sem/rpsm/oid/193192/catOid/-12973/rpem/ccd/productDetail.do")

---

