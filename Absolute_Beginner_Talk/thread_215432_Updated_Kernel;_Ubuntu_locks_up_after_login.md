---
title: "Updated Kernel; Ubuntu locks up after login"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Dural on 2006-07-13
Recently, I updated the Linux kernel through the Update Manager. Everything was fine until I restarted my computer. Now, whether I use the old kernel (2.6.15-23-386) or the new kernel (2.6.15-26-386), Ubuntu freezes after I login. I can still move the mouse cursor on screen, but the information that normally appears while Ubuntu loads into the desktop never shows up.

Computer Specs:
Processor: AMD Sempron 3100+ (1.89 GHZ) 
Memory: 1.0 GB
Video Card: NVidia GeForce 4 128 MB
Hard Drive: IDE w/ 40 GB
System setup: Dual-Boot w/ Windows XP SP2

---

### Post by compbrain on 2006-07-15
> **Dural said:**
> Recently, I updated the Linux kernel through the Update Manager. Everything was fine until I restarted my computer. Now, whether I use the old kernel (2.6.15-23-386) or the new kernel (2.6.15-26-386), Ubuntu freezes after I login. I can still move the mouse cursor on screen, but the information that normally appears while Ubuntu loads into the desktop never shows up.

Computer Specs:
Processor: AMD Sempron 3100+ (1.89 GHZ) 
Memory: 1.0 GB
Video Card: NVidia GeForce 4 128 MB
Hard Drive: IDE w/ 40 GB
System setup: Dual-Boot w/ Windows XP SP2

Hi,

When you boot up, are you getting a black/white (sort of greyish) screen with an X cursor?

Can you try and boot into recovery mode (from the grub menu) and grabbing some logs?
Stuff like:
/var/log/messages
/var/log/gdm/*
... should be the most useful.

---

### Post by coolclassic on 2006-07-15
My last update affected my nvidia settings and rewrote the xorg.conf file. I would sudjest checking xorg.conf first to see if you have the correct driver and if that doesn't work reinstall the nvidia drivers.

---

### Post by Dural on 2006-07-15
compbrain: Okay, I'll get the logs and write them down.

UPDATE: I entered the rescue mode for the new kernel, but when I typed in/var/log/messages, the response was there was no file or directory with that path. And when I tried /var/log/gdm/*, I could not access it because I did not have the right permissions. 

coolclassic: Is there a way to check the xorg.conf without logging into the desktop?

---

### Post by coolclassic on 2006-07-16
In rescue mode make your way to the etc folder in there you will find the X11 folder this is where you will find xorg.conf

---

### Post by Dural on 2006-07-19
Today, I found the xorg.conf file under /etc/X11/xorg.conf . The response was:
bash: /etc/X11/xorg.conf: Permission denied

I also got this response when trying the earlier suggestion of typing the locations /var/log/gdm/* & var/log/messages . Is there a specific password (like a root password)?

---

### Post by coolclassic on 2006-07-19
To move between directories you use the cd command.
cd /etc/X11

To see the files in a dir use the ls command

To edit a file
vim /etc/X11/xorg.conf

A word of warning learn how to use vim before using it. It is not user friendly.

---

### Post by Dural on 2006-07-19
> **coolclassic said:**
> To move between directories you use the cd command.
cd /etc/X11

To see the files in a dir use the ls command

To edit a file
vim /etc/X11/xorg.conf

A word of warning learn how to use vim before using it. It is not user friendly.

Used the ls command to view /etc/X11, then used it again to view xorg.conf. 

etc/X11/X11 --> bash: "" is a directory
etc/X11# ls --> displayed a list of files with the colors cyan, purple, green, & white: Cyan (X & gdm), White (Xsession.options, rgb.txt, Xwrapper.config, default-display manager, xorg.conf), Purple (cursors, Xresources, xinit, app-defaults, fonts, skb, Xsession.d, config), & Green (Xsession)

What if I just want to check the settings in xorg.conf, not edit them?

---

### Post by Skia_42 on 2006-07-19
If you want to just view the xorg.conf file use this command:
> sudo cat /etc/X11/xorg.conf
If you want to edit the file use this command:
> sudo nano /etc/X11/xorg.conf

---

### Post by Dural on 2006-07-19
> **compbrain said:**
> Hi,

When you boot up, are you getting a black/white (sort of greyish) screen with an X cursor?

Can you try and boot into recovery mode (from the grub menu) and grabbing some logs?
Stuff like:
/var/log/messages
/var/log/gdm/*
... should be the most useful.

Tried to grab some logs using su and sudo, but I did not have the proper permissions. 

When I boot into ubuntu, the login screen is normal and everything is fine until right after. Where there would normally be a picture showing the various services loading in the background, instead the screen is brown and my cursor (currently an enlarged red arrow) displays. I can still move the cursor, but ubuntu freezes before it can enter the desktop. 

> **Skia_42 said:**
> If you want to just view the xorg.conf file use this command:
sudo cat /etc/X11/xorg.conf


Thanks for the advice. I used it to check and see if my settings were okay and they seem fine.

---

