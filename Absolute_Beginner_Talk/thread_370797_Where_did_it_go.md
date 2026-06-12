---
title: "Where did it go??"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by defenestratos on 2007-02-26
My 80 gig Fujitsu Hard drive enclosure has stopped being recognised on both my Ubuntu 64 computer and my lovely ladie's Mac 0SX machine. The light shows on the drive which means power is getting to it... I hesitate to say it is stuffed because it is only 2 months old. It used to simply appear on the desktop.
Any way I can run diagnostics on the drive when ubuntu doesn't seem to know its there?

---

### Post by george29 on 2007-02-26
1st thing to check is if it is actually being seen by your OS. check to see if the drive can be found with gparted when it is plugged in.

---

### Post by dickinsd on 2007-02-26
In Ubuntu if you open a terminal and type **mount -a** does anything happen regarding the external HDD? 

(mount -a will mount all filesystems listed in fstab)

---

### Post by george29 on 2007-02-26
> **dickinsd said:**
> In Ubuntu if you open a terminal and type **mount -a** does anything happen regarding the external HDD? 

(mount -a will mount all filesystems listed in fstab)

that would only help if the drive was added to /etc/fstab.... 

if it's an external hard drive being picked up by pmount then there won't be an entry in fstab for the drive. (or am i wrong?)

---

### Post by defenestratos on 2007-02-26
> **dickinsd said:**
> In Ubuntu if you open a terminal and type **mount -a** does anything happen regarding the external HDD? 

(mount -a will mount all filesystems listed in fstab)


Nor Gparted or mount -a yielded ubuntu noticing the drive. The little motor in the drive is going, but when I ran the command the loading light did nothing and the motor did not change pitch...hmmm

---

### Post by george29 on 2007-02-26
hmmm... not looking good. can you get the drive out of the enclosure? if you can - try plugging it directly into your pc. will probably be an IDE connection so you should be able to connect it without a problem. if you don't have a spare ide cable or power supply inside the PC, swap out a CD/DVD drive. Gparted should see the drive if it is functional whether it is mounted or not.

it may be the controller board in the enclosure has failed and that the drive itself is still ok..

---

### Post by Tomosaur on 2007-02-26
If it's the same on both machines, I would suggest that there is something wrong with drive itself. It could, however, be the cable which connects your drive and your machine, so swap that before you go buying a new drive.

---

### Post by defenestratos on 2007-11-24
I heard that sometimes on laptops the problem is that the computer can't send enough power to the drive to make it go. I'm on route now to buy a usb hub with power to see if that helps.

---

