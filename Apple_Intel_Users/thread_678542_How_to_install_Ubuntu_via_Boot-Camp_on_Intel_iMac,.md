---
title: "How to install Ubuntu via Boot-Camp on Intel iMac, Mac OS X 10.5"
date: 2008-01-26
forum: Apple Intel Users
---

### Post by tmtoth345 on 2008-01-26
I can't find any guides online for my problem. I want to install Ubuntu 7.10 via Boot-Camp on my Intel Core 2 Duo iMac 2.0 GHz with 1GB of RAM. I have used Boot-Camp recently with Windows XP, but I removed the partition, I noticed during the Boot-Camp install for Windows that it required the Windows CD, will it take the Ubuntu Live CD? I am sorta new to Linux, I haven't used it in years and many things seemed to have changed, and even then I was still new to Linux. Is there a good step by step descriptive guide for installing Ubuntu on my iMac with Boot-Camp? I don't want to have to erase my drive or anything, but I do have and external hard drive though. Are there any known problems with Ubuntu concerning my Mac? I use Airport Extreme Wireless-N for my internet, will it work immediately when I install it, it is OK if my Wireless-N doesn't work at first but I really would like to have Wireless-N working instead of Wireless-G. I use WPA-2 for security. I think I covered everything. One more thing, will I be able to switch partitions at startup with the option key or will I have to install some startup splash screen? I look forward to coming back to the Linux community. I'll try to keep you updated.

Thanks in advance.

---

### Post by tmtoth345 on 2008-01-26
I forgot to add this, will Ubuntu take advantage of my dual cores?

Thanks

---

### Post by cyberdork33 on 2008-01-26
> **tmtoth345 said:**
> I can't find any guides online for my problem. I want to install Ubuntu 7.10 via Boot-Camp on my Intel Core 2 Duo iMac 2.0 GHz with 1GB of RAM. I have used Boot-Camp recently with Windows XP, but I removed the partition, I noticed during the Boot-Camp install for Windows that it required the Windows CD, will it take the Ubuntu Live CD? I am sorta new to Linux, I haven't used it in years and many things seemed to have changed, and even then I was still new to Linux. Is there a good step by step descriptive guide for installing Ubuntu on my iMac with Boot-Camp? I don't want to have to erase my drive or anything, but I do have and external hard drive though. Are there any known problems with Ubuntu concerning my Mac?

It's not quite that simple, but you don't have to erase the hard drive. Use bootcamp to create a partition for windows. Boot up the Ubuntu LiveCD (holding c or option to choose it). And use the Partition Editor application to delete the last partition on the disk (the windows partition). Quit the partition editor and start the installer. When prompted about where to install, choose to install to the free space.

> **tmtoth345 said:**
> I use Airport Extreme Wireless-N for my internet, will it work immediately when I install it, it is OK if my Wireless-N doesn't work at first but I really would like to have Wireless-N working instead of Wireless-G. I use WPA-2 for security.
Unfortunately, you Wi-Fi card chipset is made by Broadcom. There are no fully open drivers for Broadcom hardware. You will need to use ndiswrapper which "wraps" a windows driver to get your Wi-Fi working in Linux.

> **tmtoth345 said:**
> One more thing, will I be able to switch partitions at startup with the option key or will I have to install some startup splash screen?You can just hold Option at startup to choose what OS to boot. I would really recommend rEFIt though (or at least try it out).

> **tmtoth345 said:**
> I forgot to add this, will Ubuntu take advantage of my dual cores?

Of course!

---

### Post by tmtoth345 on 2008-01-26
Thanks

---

### Post by tmtoth345 on 2008-01-26
When I installed I am getting exactly the same problem as this person is. I burnt it twice to make sure. [http://ubuntuforums.org/showthread.php?t=632041](http://ubuntuforums.org/showthread.php?t=632041) I am going to move to this thread.

Thanks for your help cyberdork!!! (I don' mean that in a bad way) :)

---

### Post by cyberdork33 on 2008-01-26
> **tmtoth345 said:**
> When I installed I am getting exactly the same problem as this person is. I burnt it twice to make sure. [http://ubuntuforums.org/showthread.php?t=632041](http://ubuntuforums.org/showthread.php?t=632041) I am going to move to this thread.

Thanks for your help cyberdork!!! (I don' mean that in a bad way) :)
He has different hardware than you. 
Did you already install, or can you not boot up the cd at all? If you have already installed, the system will try to use the open source ati driver (which will not work). You need to install the proprietary driver. You should be able to switch to a terminal after the system has booted by using a CTRL+ALT+Fx key combo. (where Fx is F1, F2, F3, etc). How to get the right driver depends on which iMac you have. Is it an Aluminum one or an older white one?

---

### Post by tmtoth345 on 2008-01-27
Sorry for the late post, I have the older white one. I got it RIGHT before the aluminum ones came out. Here are my specs, 17 inch screen, 2.0 GHz Intel Core 2 Duo, 1 GB of memory, Ati Radeon X1600, I know I have a broad-com airport card but I don't know the model however the firmware version is Broad-com BCM43xx 1.0 (4.170.25.8). When I try to boot off the live cd after the system loads (the progress bar at startup) I see a the desktop for like a mili second with lots of horizontal line running through it, then a grey screen pops up saying it tryed to do something 6 times but failed and is waiting 2 minuets to try again. after 2 minuets nothing even happens. just as a reminder of what happened. how do i enable this ati driver thing? So should I do the alt install? Sorry for all the questions :)

thanks

---

### Post by cyberdork33 on 2008-01-27
login at the console and and edit the xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```

Look for the Device section, where it sets the "Driver" change the value to "vesa" then use CTRL+X to close nano (and choose Y to save). Then restart and you should get a desktop. From there you can use the restricted driver manager to install the fglrx driver (or you can get envy to install an even newer version of it).

---

### Post by tmtoth345 on 2008-01-28
Thank You!!!!!!!

---

