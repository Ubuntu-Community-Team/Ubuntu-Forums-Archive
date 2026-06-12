---
title: "Need Help With Graphics Driver and Reconfiguring X Server"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by fettster on 2008-02-17
I am trying to reconfigure my X server and I don't know which video card driver to choose.  I went to the Device Manager and here is what I learned about the card:

**Vendor:** S3 Inc.
**Device:** ProSavage KM133
**Status:** Status
**Bus Type:** PCI
**Device Type:** Unknown
**Capabilities:** Unknown



I am guessing that it will be either the "s3" or the "savage" driver, but I don't know which one.  

Please someone help me out, because last time I tried to reconfigure the X server (on my other computer) I screwed something up, far beyond what I was capable of fixing, so I had to completely reinstall Ubuntu.

---

### Post by overdrank on 2008-02-17
> **fettster said:**
> I am trying to reconfigure my X server and I don't know which video card driver to choose.  I went to the Device Manager and here is what I learned about the card:

**Vendor:** S3 Inc.
**Device:** ProSavage KM133
**Status:** Status
**Bus Type:** PCI
**Device Type:** Unknown
**Capabilities:** Unknown



I am guessing that it will be either the "s3" or the "savage" driver, but I don't know which one.  

Please someone help me out, because last time I tried to reconfigure the X server (on my other computer) I screwed something up, far beyond what I was capable of fixing, so I had to completely reinstall Ubuntu.

HI and why are you trying to reconfigure your xorg? Is the resolution the issue. I would say the savage driver or you could use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and this will do it automatically

---

### Post by Presto123 on 2008-02-17
*Edit* No need for my post.

---

### Post by fettster on 2008-02-17
Thank you for your advice, and to answer your question, no its not the resolution.  I don't have the driver for my video card, and therefore cannot use anything related to OpenGL or Desktop Effects.  

Also, if there is a better or easier way to fix my problem, then i will gladly do it, but I'm actually in the middle of reconfiguring the X server.  Is there any way to cancel the reconfiguration.  I made a backup of the X server before I started by using "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup"   I got this command off another link in the Ubuntu Forums.

And, I am typing this on a separate computer, so I will be able to make any changes necessary and still be able to follow the instructions you give me.  

Thanks, again.

---

### Post by overdrank on 2008-02-17
> **fettster said:**
> Thank you for your advice, and to answer your question, no its not the resolution.  I don't have the driver for my video card, and therefore cannot use anything related to OpenGL or Desktop Effects.  

Also, if there is a better or easier way to fix my problem, then i will gladly do it, but I'm actually in the middle of reconfiguring the X server.  Is there any way to cancel the reconfiguration.  I made a backup of the X server before I started by using "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup"   I got this command off another link in the Ubuntu Forums.

And, I am typing this on a separate computer, so I will be able to make any changes necessary and still be able to follow the instructions you give me.  

Thanks, again.
Hi and if the reconfigure does not work then yes you can restore your backup. I really doubt you will enable the effects with that graphics. 
To copy Xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
To restore backup
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by fettster on 2008-02-17
Thank you so much.

I apologize for the persistent questions, but what would happen if I simply closed the root terminal that I am running the X server reconfiguration in?  Would that let me escape the reconfiguration process so that I could try the command that you mentioned in your first post, or restore the X server with the command that you mention in your last post?

---

