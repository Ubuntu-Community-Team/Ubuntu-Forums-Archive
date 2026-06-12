---
title: "Triple Boot"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by negrix on 2007-11-17
Ok Guys ... Need some advice

I have XP on first hard drive, Vista on 2nd hard drive and Ubuntu on my usb hard drive, 
I want to install ubuntu on a different partition on the second hard drive. Is there a way to transfer ubuntu (or save my settings) from the usb drive to the 2nd hard drive.??

Thank you very much !!

---

### Post by Six_Digits on 2007-11-17
So you are constantly booting from USB for Ubuntu? It Is a USB hard drive, right? Either way, plug in the live cd at startup, and follow directions until the partitioning step. At this point, follow procedures for your expectations. I.E., Resize "Volume 2" (whatever your USB drives mounted at) into two partitions, the latest partition will be for linux. Using the guided install is best,  but otherwise, you'll need 3 partitions for Linux total, "/", "swap", and "boot".

---

### Post by negrix on 2007-11-17
I was... I just added the second hard drive and installed Vista on it. Now I want to install Ubuntu on that drive (I left some room for it). But I already have Ubuntu configured the way I want to in the usb drive. Do I need to reinstall ??

---

### Post by integr8e on 2007-11-17
Yes there is.  You may have to resize the Vista partition on your second hard drive, check out [**How to resize a partition**](http://gparted.sourceforge.net/larry/resize/resizing.htm) with [**GParted**](http://gparted.sourceforge.net/).

Then, you will want to use a disk cloning utility like [**PartImage**](http://www.partimage.org/Index.en.html) or [**g4l**](http://sourceforge.net/projects/g4l) (Ghost for Linux) to copy the contents of your USB drive to your hard drive (NOTE: you must create a partition on your hard drive either equal to or larger than that of your USB drive for any of the utilities to work).

Once you have finished, you may need to modify your /boot (GRUB) entry.  Check out Qqmike's [**HOW TO: GRUB Methods - Toolkit**](http://kubuntuforums.net/forums/index.php?topic=3081671.0).  You can either modify it manually or with a graphical tool called StartUp-Manager - startupmanager - which is the easiest solution.

Edit: Sorry, I was working on this while y'all posted the above . . .

---

### Post by negrix on 2007-11-17
Great !! I will give that a try and let you know !

Thanks for the quick replies !

---

### Post by Inxsible on 2007-11-17
yeah. i would first format the drive to ext3 and then use partimage to copy over the stuff from your usb to the partition.

---

### Post by integr8e on 2007-11-17
> i would first format the drive to ext3 and then use partimage to copy over the stuff from your usb to the partition.

Thanks Inxsible, I forgot to mention that detail.

---

### Post by Inxsible on 2007-11-17
> **integr8e said:**
> Thanks Inxsible, I forgot to mention that detail.
was that sarcasm?   :-|

Maybe not.

you would first have to make a bit by bit image of your usb drive using partimage and then use that image to put it on your new drive. here's a tutorial that will help you create a partimage of your ubuntu install and then use that to explode into your new drive.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by negrix on 2007-11-17
That sounds like a good idea. Its a 320GB drive... formatted only 100GB for Vista and the rest is "unallocated".

Thanks for all the Help !!

---

### Post by integr8e on 2007-11-17
> was that sarcasm?

No, I was being serious.  I'm sorry if you took it that way, I don't usually respond to anything sarcastically.

---

### Post by rsambuca on 2007-11-17
A few things...

negrix - you will have to edit both your /boot/grub/menu.lst and your /etc/fstab to get things working properly.

integr8e - Just for your reference, the recommended course of action when resizing Vista is to use Vista's own Disk Manager to "shrink" the Vista partition.  There have been a lot of Vista partitions rendered unbootable from the gParted partitioner.

---

### Post by Inxsible on 2007-11-17
> **integr8e said:**
> No, I was being serious.  I'm sorry if you took it that way, I don't usually respond to anything sarcastically.
Yeah that's what I thought.

At first read, it looked like sarcasm...but on reading it a couple of times more I knew what you meant. That's why I mentioned "Maybe not" :D


you know how it happens sometimes. I didnt remove my "was that sarcasm" comment because i had already posted it.

Sorry for the confusion mate !!

:)

---

### Post by integr8e on 2007-11-17
- ***Inxsible***
> ...but on reading it a couple of times more I knew what you meant.

Thanks.

 - ***rsambuca***
>  . . . the recommended course of action when resizing Vista is to use Vista's own Disk Manager

I didn't know that, I'm glad you pointed it out :-D

---

### Post by integr8e on 2007-11-17
Err, sorry, duplicate message . . .

---

