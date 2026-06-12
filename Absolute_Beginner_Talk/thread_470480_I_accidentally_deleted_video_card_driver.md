---
title: "I accidentally deleted video card driver"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-11
I finally got ubuntu set up nicely and figured that I could enhance the video by following the code in the sticky about ATI video card driver support. [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)  Big mistake.    I have an ATI x1900 xtx PCIe video card.  After adding the code changes, a box popped up in ubuntu stating something about restricted drivers.  I said okay.  After awhile i noticed that the video looked worse after making the changes so I disabled the box where it said restriced drivers and then the system prompted me to reboot.  I tried to reboot but never got the system up and running again and saw some errors about video drivers being removed on a DOS like blue screen. :(  Is there any way to reinstall the orignal drivers with out installing Ubuntu all over again?   Any help will be appreciated.

Thx in advance,

VC

---

### Post by Outrunner on 2007-06-11
While the blue error is flashing press CTRL-ALT-F2 and login with your username/password. Type

```
sudo nano /etc/X11/xorg.conf
```

Use the arrow keys to get down to the "Device" section and navigate to where it says Driver and change the quoted word to "vesa". Press CTRL-X and 'y' to save the file. 

```
startx
```

Should get you back to the GUI

---

### Post by videocheez on 2007-06-11
Thanks man.  I got my gui back.  Now, I'm going to try envy to install the correct ATI drivers.  I f you have any advice before i finish downloading the ATI drivers it would be appreciated.

Thx,

VC

---

