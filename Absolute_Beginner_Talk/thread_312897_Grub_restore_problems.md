---
title: "Grub restore problems"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-05
Hi I've recently installed Ubuntu: Draker 6.06 with / on my **hda** and /home + /swap on my **hdb drive**.  I've spent almost a month configuring it correctly and installing all the neccessary programs to make it workable on my machine.

Now just yesterday I re-installed Windows XP for my gaming needs.  By doing a dual boot setup on my hda drive.  Which of course wiped out my Grub on MBR.  I wasn't suprised.

So now I wanted to restore Grub so I followed this tutorial with 
**Arnieboy>>>**[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)
But I could only get to **step 5**, in Draker Live CD it seems that if you don't re-format your old working partitions you won't have permission to continue on with the installation. :( 
So you see I don't really want to re-format all the configuration work and program install I did the last 5 weeks, by formating my separated root and home partitions.

**Yesplease>>>**
had an A:\ drive tutorial on restoring Grub but it was too technical for me to follow.

**Shirishag75>>>**
So instead I followed Shirishag75s **Old skool tutorial** which seemed like the least hassle free Grub restore method.
But of course I had to run into problems even with such an easy tutorial :( 
When I followed his steps all to the end where you type in:
**grub-install /dev/hda **I even tried grub-install /dev/hda3 which is where my Linux / partitions lies.  I get this:
> Probing devices to guess BIOS drives.  This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by daniminas on 2006-12-05
Start your live Cd:

Try mount your partition from the live cd 

> sudo  mount /dev/hda0 /mnt

sudo grub
grub> find /boot/grub/stage1
(hd0,2)
grub> root(hd0,2)
grub> setup(hd0)
grub> quit

> sudo reboot

---

### Post by indytim on 2006-12-05
Or, another alternative:

A. Burn to CD SuperGrub [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")
B.  Boot to the CD
C.  Repair your Grub.


IndyTim

---

### Post by jingo811 on 2006-12-05
**Daniminas** you are a true Linux GOD [-o< 
Your ultra-light-tutorial fixed things quick and painless.  I'm back surfing on Ubuntu again, I'd never thought I would miss Linux this much...maybe I've been turned from the darkside (Microsux) for real this time :p

---

