---
title: "I DIDN'T install Ubuntu and can't boot properly!"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by catwhowalks99 on 2008-11-13
Hi there...

I apologize in advance if this question has been asked before.  I couldn't find any reference to it...

I have a MacBook which I bought in October of 2007.  A few hours ago, I downloaded Ubuntu 8.1 and created a partition for it using Boot Camp.

From the installation screen (I burned Ubuntu to a DVD) I first checked the CD for errors.  My Mac found none.  Then, I selected the 'USE UBUNTU WITHOUT CHANGING YOUR SYSTEM' option.  Ubuntu came up a minute later and I was able to use it with no problems.

However, I realized that there didn't seem to be any option for going back to OSX, so I figured I would just shut down Ubuntu and my Mac would reboot into OSX.

I shut down and was taken back to the installation option screen... where I found nothing on returning to OSX.  I shut down and the disc ejected.

So here's the problem:

When I powered back up, the screen turned the normal grey, but then went black.  A messagetells me 'THERE IS NO BOOTABLE DRIVE...' (or something like that).

I tried booting again, but this time started up and held down the OPTION key and then manually selected my internal drive.  I am now able to start up and get into OSX, but I ALWAYS have to hold the OPTION key down and select my internal drive.

I used Boot Camp to remove the partition, thinking my Mac was somehow confused, but I am still unable to boot except through using the OPTION key and selecting my internal drive.

What did I screw up?  I know there's something really simple going on here that I'm missing (I'm not a computer savvy guy... sorry...).

Thank you very much, and again I am sorry if this question is ridiculously simple or has already been answered somewhere else.

Matt

---

### Post by cyberdork33 on 2008-11-13
boot into OSX and in System Preferences, use the "Startup Disk" selector to reselect OSX as the default OS. It sounds like you did this to boot from the CDROM in the beginning, but this sets it as THE boot device until it changed again (which you cannot do in Ubuntu).

If you are planning to install Ubuntu to your extra partition:

In OSX, install rEFIt!

boot with the option key and start the Ubuntu LiveCD.

Start gparted (partition editor) in System > Adminstration and delete the partition you made with BootCamp (it is the partition after the HFS+ partition (OSX).  This will leave a large blank space on the disk. Make sure yo click apply then exit the partition editor.

Now start the Ubuntu installer. When prompted, choose to install to the "largest free space" and on the last screen of the installer, click "Advanced" and choose to install GRUB to your Ubuntu root partition (likely /dev/sda3).

After it is done installing you will need to follow the steps here:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by catwhowalks99 on 2008-11-14
Thank you very much for such a quick reply!  

It was so late and I was so frustrated with the whole thing I went and Time Machined my MacBook.  I'm sure what you said was probably the problem, though.  Thanks again for your reply.

I have another question, though, if you don't mind: why would Ubuntu give the user a 'sample' mode without a clear way to get out of it and return to your original system?

Or did I just do something really stupid?

Matt

---

### Post by catwhowalks99 on 2008-11-14
Ah, never mind... I just read the link you posted... 

A BUG IN THE SYSTEM!  Aha!

I feel better... maybe I'm not so stupid after all...

Matt

---

### Post by cyberdork33 on 2008-11-16
> **catwhowalks99 said:**
> I have another question, though, if you don't mind: why would Ubuntu give the user a 'sample' mode without a clear way to get out of it and return to your original system?

Or did I just do something really stupid?

Just booting from the Ubuntu CD does not cause any change to your computer. What I am GUESSING you did was use the "Startup Disk" utility in System Preferences to choose to boot from the CD. Unfortunately, there is no equivalent utility to switch it back to OSX from within Ubuntu. The bug I posted about is only applicable if you actually install. When you would like to boot a Linux CD, be sure to just insert the disc, power down the Mac, and then startup while holding the Option key. That will give you the option to boot from the CD only for this session.

Good Luck!

---

