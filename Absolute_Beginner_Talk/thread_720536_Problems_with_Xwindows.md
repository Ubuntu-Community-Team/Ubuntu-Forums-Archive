---
title: "Problems with Xwindows"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by AndyGreen1026 on 2008-03-10
Hi all,

I recently installed Ubuntu V7.10 alternate i386 to my Toshiba X3000 laptop, as I really want to get started with Linux.

I am not having any luck getting the graphical interface to display. The ubuntu bar and logo come up , bit when it gets to the end, the screen goes blank. Similarly it reappears if I shut down

I can go to the command line version OK using alt-ctrl-F1, and log in and out etc. however, it only occupies a small square (about 1/2 width x height) of the screen in this mode

I suspect that it is a problem frame buffers, as I get similar problems when trying to use the systemrescue CD. However, Knoppix loads and works fine. at full screen. The native resolution of the laptop is 1024 x 768.

I have tried using the dpkg-reconfigure xorg-xsever command, but I eventually messed up something, and it wouldn't even show the command lien!

I 'flattened the PC, reformatted it and reinstalled Ubuntu, this time, only selecting 1024 x 768 and the three other lower resolutions. Still no joy. So before I mess it up again, has anyone any ideas how I can sort out this problem - Is there any way, for example to copy or figure out a setting from the working Knoppix boot CD version to my Ubuntu setup?
Any help gratefully appreciated

Andy

---

### Post by handydan918 on 2008-03-10
> So before I mess it up again, has anyone any ideas how I can sort out this problem - Is there any way, for example to copy or figure out a setting from the working Knoppix boot CD version to my Ubuntu setup?
Sure, it can be done. I don't know if it will work...but then what you have now doesn't work anyway, does it?
1) Boot Knoppix ( or maybe better, a Mepis cd...the Debian base may make it closer to Ubu...)
2) mount the root partition of your Ubu installation, and go to /etc/X11/xorg.conf
3) Rename this file as something else for backup purposes, i.e., xorg.bak
4)Copy the Knoppix or Mepis xorg file over to the /etc/X11 directory on the hard drive.
5)Reboot and cover your ears to prevent deafness from the loud cursing you may hear.

:popcorn:

---

### Post by JoshuaRL on 2008-03-10
Could you post your specs?  I know you said the type of laptop, but I couldn't find specs online for some reason.

I think you're right, sounds like a misconfigured Xorg.

And if you boot into Recovery Mode you could try:
```

dpkg-reconfigure -phigh xserver-xorg

```

---

