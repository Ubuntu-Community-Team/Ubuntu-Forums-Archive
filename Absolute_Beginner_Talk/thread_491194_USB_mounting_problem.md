---
title: "USB mounting problem"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by DasMatts on 2007-07-03
Howdy all, 

I am running FF on a IBM t40 laptop. I am having trouble mounting my usb key in the port. Every once and awhile I will insert it and it will mount automatically, but the other 95% of the time my computer does not even show there is anything there. Any ideas?

Cheers, 

Matt

---

### Post by Inxsible on 2007-07-03
> **DasMatts said:**
> Howdy all, 
 
I am running FF on a IBM t40 laptop. I am having trouble mounting my usb key in the port. Every once and awhile I will insert it and it will mount automatically, but the other 95% of the time my computer does not even show there is anything there. Any ideas?
 
Cheers, 
 
Matt
you can create a permanent mount point for the drive, instead of using the regular disk, disk-1 etc. that Ubuntu makes for you when you connect the drive.
 
do a ```
sudo fdisk -l
``` -l is lowercase L. Use the device name for the USB stick in the next command
you can use pmount to mount it
 
```
sudo pmount /dev/Xd*? usbdrive
```where X = s or h
* = a,b,c,d......
? = 1,2,3,4.....
 
 
Hope that helps !

---

### Post by DasMatts on 2007-07-03
I am trying to follow the instructions you gave me and i am hitting a snag, probably on my part not fully understanding (still new to all of this, damn windows and their lazy brainwashing)

I am assuming that i pick the name of the mount point on my drive. i typed this in:

sudo pmount /dev/sdb4 usbdrive

What came up was:

sudo: pmount: command not found. 


What am I doign wrong? Also, when I entered the command: "sudo fdisk -l"  with and without the USB key in the drive i got the same result. Is this a problem? should it not be reading the drive is in there?

---

### Post by Mr.Beast on 2007-07-03
> **DasMatts said:**
> Howdy all, 

I am running FF on a IBM t40 laptop. I am having trouble mounting my usb key in the port. Every once and awhile I will insert it and it will mount automatically, but the other 95% of the time my computer does not even show there is anything there. Any ideas?

Cheers, 

Matt

Hi Matt, 
I don't wish to be the harbringer of doom and dispair, but linux issues aside, it is quite a common symptom to see IBM T series laptops degrading from USB 2.0 ports to USB1.1 / 1.0 ports, and this is normally a sign of impending Motherboard failure.

Of course, it may not be, but worth bearing in mind as well.

---

### Post by Inxsible on 2007-07-03
> **DasMatts said:**
> I am trying to follow the instructions you gave me and i am hitting a snag, probably on my part not fully understanding (still new to all of this, damn windows and their lazy brainwashing)
 
I am assuming that i pick the name of the mount point on my drive. i typed this in:
 
sudo pmount /dev/sdb4 usbdrive
 
What came up was:
 
sudo: pmount: command not found. 
 
 
What am I doign wrong? Also, when I entered the command: "sudo fdisk -l" with and without the USB key in the drive i got the same result. Is this a problem? should it not be reading the drive is in there?
 
You probably dont have pmount installed. Install it by
```
sudo aptitude install pmount
```
 
About you getting the same results for both fdisks....your drive is not being recognized...Can you post both the outputs here? Also how did you guess it was sdb4 then ?

---

### Post by Inxsible on 2007-07-03
> **Mr.Beast said:**
> Hi Matt, 
I don't wish to be the harbringer of doom and dispair, but linux issues aside, it is quite a common symptom to see IBM T series laptops degrading from USB 2.0 ports to USB1.1 / 1.0 ports, and this is normally a sign of impending Motherboard failure.
 
Of course, it may not be, but worth bearing in mind as well.
 
I would second on that.... I had a T40, which degraded from 2.0 to 1.1. Thankfully, since it was a work computer, I just had my company give me a T42. When this goes down, I will ask for a T60. T60s seem pretty sweet !!!
 
I didn't know that the USB degrade was a common problem :o

---

