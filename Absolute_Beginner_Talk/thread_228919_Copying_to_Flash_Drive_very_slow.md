---
title: "Copying to Flash Drive very slow"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by tommyp on 2006-08-03
Usually (but not always) when copying files from Ubuntu to a USB flash drive, the transfer speeds are very slow and the computer gets very sluggish.  I am using a pretty old computer (P3 650mhz, 640MB RAM).

My guesses are:
1. - the USB drive is working at 1.0, not 2.0 speeds
2. - maybe two open Nautilus windows is too much for my machine (I confess I use two windows to drag and drop the files) 
3. - both

How can I find out what USB standard is being used?  Would the xfce file manager work better than the gnome version?

Thanks!

---

### Post by netstv on 2006-08-03
First thing I'd look at is are you getting any errors?  So look at /var/log/messages or dmesg to see if there is anything of interest there.

Secondly, have you tried to use just a terminal?  What I mean is that the usb stick will be mounted.  So what I would think you need to do is just copy your files from one directory to the other.

Third, I'd be interested in seeing what file system is loaded on the usb stick.  If, for example, it's ext3 with journaling it may have some verify stuff turned on, so that it will verify before it writes.

Can you reformat your usb flash as a test???  I don't know.. I have sooo many questions!  #-o

---

### Post by kadymae on 2006-08-03
> **tommyp said:**
> 
My guesses are:
1. - the USB drive is working at 1.0, not 2.0 speeds


I can **gurantee** you that it's USB 1.0.  USB 2.0 didn't come out until after the P4 had been introduced.  It doesn't matter that the drive is 2.0 capable.  The hardware of the laptop just can't push data out the port any faster than 1.0.

---

### Post by orb9220 on 2006-08-03
Yep same here with only 1.1 is only 1.5mb sec where 2.0 is 12mb sec.

---

### Post by tommyp on 2006-08-04
dmesg spewed alot of stuff.  Is there anything in particular that I should be looking for?  I'll have to check the error log.

BTW, I am connecting through a USB 2.0 pci card that's been installed.  The drivers seemed to work in windows 98 that was installed on the machine.

I'm sure the card was initialized in some windows format, so it's not an ext3.

---

### Post by BigDave708 on 2006-08-04
> **netstv said:**
> Can you reformat your usb flash as a test???  I don't know.. I have sooo many questions!  #-o

Don't do that! Some USB drives store data that they need on the drive itself and if you format it, the drive would become unusable.

It probably is the fact that you are plugging a USB 2.0 drive into a USB 1 port.

---

### Post by netstv on 2006-08-04
> **BigDave708 said:**
> Don't do that! Some USB drives store data that they need on the drive itself and if you format it, the drive would become unusable.

It probably is the fact that you are plugging a USB 2.0 drive into a USB 1 port.

Huh?  I do it all the time and it works fine.  We do it especially for flash devices we use on embedded systems.  The driver is on linux not on the drive.  But hey.. I'm no expert. I can just talk about what I've done before.  sfdisk will always get me what I want back.  ALWAYS.

If there is anything on there that is valuable, right.. don't reformat it.  

Basically in dmesg or the log file you are looking for write errors.  It will say something like /dev/hda1 (or whatever the drive is) failed to write.. some such error.

---

### Post by MaximB on 2006-08-04
I have to opposite problem
1.it's just too fast - and some files are corrupted after I copy them
what can I do ?

2.and tommyp - you might need to look into your BIOS
there supposed to be USB section - there you can choose the speed you want.

---

### Post by FizDev on 2006-08-04
> **MAXDDARK said:**
> I have to opposite problem
1.it's just too fast - and some files are corrupted after I copy them
what can I do ?


Copy your files then open a terminal and type (I think)
```
sync
```

---

### Post by Teva on 2007-07-27
I too am having a problem.  I have USB 2.0 but when writing to the flash drive it takes approximately 10 minutes to transfer a 700MB file from my computer to the flash drive. If I boot into Windoze XP and use the same USB port, the file transfer is fast. So, I know it's not the equipment. I'm relatively new to Linux so I'm not sure what to do here. Any help will be appreciated.

Thanks,


Teva

---

### Post by timcredible on 2007-07-27
you have to have a usb 2.0 card to run at 2.0 speeds (480Mb/s  max).  if you plug a usb 2.0 flash drive into a usb 1.x card, it'll run at usb 1.x speeds (12Mb/s max).  you can buy an ide usb 2.0 card on ebay for about $7, install that in your pc, and then you'll be ok.  your pc isn't fast enough to run at the full 480Mb/s, but you'll run a lot faster than 12Mb/s.

---

