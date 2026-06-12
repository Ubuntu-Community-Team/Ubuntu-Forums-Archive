---
title: "after disabling restricted drivers"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by hetihe on 2007-07-03
hi,
restricted drivers (nvidia) did not work for me, so I disabled them. Now when I try to log in, I get just white screen. 
x11.conf says that driver is "nv" What to do?
I am running 7.04 :p

---

### Post by sad_iq on 2007-07-03
Type ```
sudo nano /etc/X11/xorg.conf
``` and change the nvidia to nv...so it will look like this:

 Section "Device"
    Identifier     "nvidia whatever..."
    Driver         "nv"
    #...whatever comes next...
 EndSection

---

### Post by Dedoimedo on 2007-07-03
Hello,

Can you get to the command line when you boot?

If not, boot in failsafe mode. Edit the xorg.conf to read a generic vesa driver so you can boot into the X Windows. From there, you can try the next step of tweaking the drivers.

To reconfigure the xorg.conf file, in the command prompt, as sudo:
dpkg-reconfigure xserver-xorg

This will take you through a series of wizard questions regarding your drivers, resolution etc. Answer them correctly and you'll get your desktop back again.

Once you complete the configuration, write /etc/init.d/gdm restart to get back to the desktop.

Alternatively, to stop it when booted in graphic environment, /etc/init.d/gdm stop.

Do you understand these instructions?
Dedoimedo

---

### Post by hetihe on 2007-07-03
[QUOTE=Dedoimedo;2954772]Hello,

Can you get to the command line when you boot?

Yes I can, I just wasted my energy trying to follow the first, now edited suggestion.

To reconfigure the xorg.conf file, in the command prompt, as sudo:
dpkg-reconfigure xserver-xorg

Is there no other way, I mean reconfiguring all is so complicated.
Do you understand these instructions?

Yes I do, and thanks for both anyway

---

### Post by zero244 on 2007-07-03
In your driver line you can try vesa instead of nv that might work.
In edgy as a last resort you can delete the xorg.conf and it will boot without a xorg.conf. That has saved me on numerous occasions.
Always have a backup of Xorg.conf or several backups.
I swapped out nvidia cards the other day and nv wouldnt boot, but vesa mode did.
Then I was able to install the drivers for the new card.
You have ot use sudo nano to edit the xorg.conf file.
It will be in the /etc/X11 directory.
Also you have to use a capital X to access that directory.

---

