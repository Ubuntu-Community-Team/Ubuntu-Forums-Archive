---
title: "[SOLVED] Copying xorg.conf to a flash drive"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-09-19
Hi everyone,

What is the best way of copying an xorg.conf file to a flash drive? I'm having a few issues with my video card/getting compiz fusion to work and I've been asked to post my xorg.conf file. The problem is that I cannot get into GNOME at this stage so I have to be able to do it on the command line.

I know a few commands in the command line, (such as cd and ls) but how do you copy files? Also, where abouts does my flash drive turn up in the file system (this is obviously where I need to copy the file too)?

Thanks to anyone who has the answers.

---

### Post by Jeroen Vernooij on 2007-09-19
First, browse /media to see where your flash disk is mounted:

ls /media


then: copy xorg.conf


sudo cp /etc/X11/xorg.conf /media/USBDISK/xorg.conf


If you are running 7.10, you can just remove xorg.conf and you will get in GNOME thanks to failsafe-mode:
sudo rm /etc/X11/xorg.conf

If you are running 7.04: boot from live-disk and copy your xorg.conf from the filesystem in the livedisk to your USBDISK, then reboot without live-disk in it, and copy your xorg.conf back to your Harddisk.


Good luck

---

### Post by NovaAesa on 2007-09-19
Thankyou.


I can't actually boot from the live cd because i had to use the alternate one to install. When you said to boot from the live cd, it gave me an idea though - to bood from Damn Small Linux. I've been using an old laptop with it.

Thanks for the help!

---

### Post by Jeroen Vernooij on 2007-09-19
Good to hear.

It sucks to not be able to boot from live-cd.
It's very handy when you destroy your installation or when your harddrive dies.
You should ask support to get live-cd booting working: maybe you have to give it custom parameters or something.

---

### Post by NovaAesa on 2007-09-19
It has something to do with my graphics card (ATi Radeon X800XL), and all other Radeon X**** cards. It should be fixed in Gusty, so I'm not to worried about it.

---

