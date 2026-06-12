---
title: "No video in new Gutsy install"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by punkybouy on 2008-01-13
I installed gutsy from the alternate CD today and on the first boot up after the install I logged in and I got a 1600X1200 screen resolution on my older Dell Inspiron laptop.  Everything worked pretty well but as a laptop with a 15 inch scree 1600X1200 makes everything pretty small so I switched to 1280X1024 and this was much better.  I then went to the "System\Preferences\Appearance" section and selected the middle of the three effects available from the tab on the right.  A pop up appeared and prompted me to enable the restricted driver for Nvidia which I did.  It automatically downloaded one file which installed and then prompted me to reboot and revisit the section and again choose my effect level.  When I rebooted I got the splash screen and then nothing just black.  I did get the bongo sound and even with a black screen I could enter my user name and password.  I got the login sound at the point where the desktop would have appeared but still no video.  I should also point out I had not yet installed any updates even thought there were about 230 MB of them.  Anybody have any ideas how I can get back to the original video setting to try again?  Thanks for your help.

---

### Post by blueridgedog on 2008-01-13
You can kill the current xserver with CRT+ALT+BACKSPACE an then try and reconfigure the xserver with 
```

sudo dpkg-reconfigure xserver-xorg
```

Or, hit CTR+ALT+F2 to get another tty and reconfigure there after logging in.

---

### Post by punkybouy on 2008-01-14
Thanks for your help.  The nvidia driver does not work so I set the xorg to use the "nv" driver which got me going again.  Using the old hard drive I booted up Dapper and copied the xorg.conf to a usb drive and when I looked at it I saw that color depth was set to 16 in Dapper and not 24 so I will install the new drive with Gutsy and try the nvidia driver again but set color depth to 16.  Indeed, I may just copy in the xorg.conf and see what it does.

---

### Post by blueridgedog on 2008-01-14
Good luck.  

The Nvidia cards are supposed to be more supported than the ATI.

---

