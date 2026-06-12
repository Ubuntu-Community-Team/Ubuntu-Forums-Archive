---
title: "I think i screwed something up"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-03-31
I went into /etc/X11/xorg.conf

and added some resolutions trying to be able to use 1280x1024 in stead of  the usual 1024x758.

When I rebooted, the loader got all the way to about the end and then stopped. The screen got all weird and I can't get into ubuntu.

Pic:
[IMG]http://img503.imageshack.us/img503/5918/s4020528sr7.jpg[/IMG]

---

### Post by raja on 2007-03-31
If there is a problem because of the changes and you want to go back to your original configuration, do Ctrl-Alt-F1 to go to a terminal. Now you can use ```
nano /etc/X11/xorg.conf 
``` and then edit the file to remove the changes you made. Else, if you made a backup of the file before editing (always a good idea), you can restore it by something like ```
sudo cp /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf
```. Otherwise you can regenerate a new config file automatically by typing ```
 sudo dpkg-reconfigure -phigh xserver-xorg

```.

---

### Post by Gorthus on 2007-03-31
But I can't get in.. That screen is as far as I get on boot.

---

### Post by NikoC on 2007-03-31
Try booting in recovery mode (select it from your grub boot menu), that should get you in command line terminal to execute the procedure prescribed in the previous post.

---

### Post by raja on 2007-03-31
If only the xorg is messed up, everything else should be loaded. So try Ctrl-Alt-F1 at that point. If not, try booting in recovery mode and do this. If that too fails, you can boot up with your live cd and then change the xorg file.

---

### Post by Gorthus on 2007-03-31
Got into recovery mode and fixed it... Thanks!

Now how do I get into 1280x1024?

---

### Post by raja on 2007-03-31
Have a look at this [wiki entry]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

---

