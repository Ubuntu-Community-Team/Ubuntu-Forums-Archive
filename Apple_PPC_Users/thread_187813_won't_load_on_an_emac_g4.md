---
title: "won't load on an emac g4"
date: 2006-06-03
forum: Apple PPC Users
---

### Post by jedimdan on 2006-06-03
I know this has probably been brought up quite often, but after searching the forums, I haven't been able to find a solution to my problem.

I'm trying to boot the Kubuntu 6.06 desktop CD onto an Apple G4 (800 mhz) eMac with an Nvidia Graphics Card. It loads all the way up to the screen with the kubuntu logo, followed by a blinking cursor, then the screen goes black and stays that way. After a while, I'd hear a music play (i'm assuming it's a start-up sound) but the screen is still blank.

I've tried the instructions to modify the xorg.conf file from [http://www.ubuntuforums.org/showthread.php?t=95545&highlight=screen+blank](http://www.ubuntuforums.org/showthread.php?t=95545&highlight=screen+blank) by changing the horizontal and vertical refresh rate to the one mentioned (HorizSync to 70-73, VertRefresh to 70-140) then it will go to the kubuntu loading screen again, a blinking cursor for a long time, and stay that way. How can I get it to work and what settings other than the refresh rates do I have to change? 

Also, I noticed that the kubuntu logo during the loading screen looks off-coloured, like as if it's inverted. Does that mean anything?

Hope someone can help me.

---

### Post by Ptero-4 on 2006-06-03
Do you have OSX in that eMac? If you have install Apple X11.app (it's on the Install DVD or install CD3). Then run it and type this in Terminal.app or a xterm:
```
cp /etc/X11/XF86Config-4 ~
```

This will copy the Apple's X11.app config file to your home folder.
Then reboot into ubuntu, when the screen goes blank press ctrl-option-f1 to go to a command line, log in with your usename/password you created when you installed kubuntu, mount your OSX partition (use sudo fdisk -l /dev/hda to see which one is it) by typing:
```
mount -t hfsplus /dev/hdaN /mnt
```
Then copy the XF86Config-4 file to your home folder typing:
```
cp /mnt/Users/username/XF86Config-4 ~
``` where username is the name of your OSX home folder.
And then copy the pertinent values from the XF86Config-4 file to the /etc/X11/xorg.conf file (Note: don't copy the XF86Config-4 file over the xorg.conf one, they have slightly different layouts).
And if you ask. What you're doing is simply getting OSX to find and write down the correct X11 video settings and then using them in ubuntu.

---

### Post by jedimdan on 2006-06-04
The problem is I don't have Mac OS X on this machine. I got this machine from a friend who didn't want it anymore, but she lost the restore disk and this emac had a damaged hard drive which I had finally replaced with a new one. That's why I'm trying to install Kubuntu onto it, so that I put it to some good use :D

Any way I can get the settings without entering Mac OS X?

---

### Post by 3rdalbum on 2006-06-04
You might need to change the driver setting.

When you open the xorg.conf file, what does it say under Section "Device"?

Try changing the Driver part to "nv" if it isn't already. Also try "vesa" and "vga".

And yes, the sound you are hearing is the startup sound. One of them, at least.

---

### Post by jedimdan on 2006-06-04
Ptero-4:
I found a copy of an X11 config file for an emac similar to mine from this page:
[http://ubuntuforums.org/showthread.php?t=924&highlight=emac](http://ubuntuforums.org/showthread.php?t=924&highlight=emac)

and followed what you said by just adding in or changing stuff that's different and now I can get into Kubuntu! Thanks a lot!! :D 

It turns out the missing stuff is the "ModeLine" part for the monitor and moved the "Option: "DPMS"" from the monitor to Device section and worked! Just out of curiousity, what are those two things?

---

