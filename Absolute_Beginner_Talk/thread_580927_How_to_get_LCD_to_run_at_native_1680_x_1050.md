---
title: "How to get LCD to run at native 1680 x 1050"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-10-19
Although in Feisty the ATI driver was not working I could run at 1680 x 1050.  The upgrade to Gutsy has totally ruined my display (out-of-the-box, yeah right) and it is now using the vesa driver.

How can I get my display back to 1680 x 1050?  I have an ATI X1300; is there a generic open source ATI driver I should be using?

Thanks.

---

### Post by Kosimo on 2007-10-19
Witch video card do you have?
Did you try installing the restricted drivers?

---

### Post by DrQuincy on 2007-10-19
Yes, spent five hours yesterday messing with trying to get the ATI dirver working.  I have X1300 ATI.

---

### Post by Tom Mann on 2007-10-19
in the console/terminal type:

```
sudo nano /etc/X11/xorg.conf
```

go down to the section where all the display modes are written (ie "1280x1024" "1024x768" "800x600"...), and add "1680x1050" before the first resolution in each line.

when you're done, restart X and it should start in 1680x1050.

:)

---

### Post by DrQuincy on 2007-10-20
He has that already.  When I reconfigure xserver-xorg it auto detects the monitor fine and gets all the correct resolutions but when you restart X it has reverted to the vesa drive and a message comes up saying it cannot detect the hardware and so is running in low-graphics mode.  Any ideas?

---

### Post by Qwerty_ on 2007-10-20
Are you able to do anything from with in System>Administration>Screens and Graphics?

---

### Post by DrQuincy on 2007-10-21
> **Qwerty_ said:**
> Are you able to do anything from with in System>Administration>Screens and Graphics?

Whatever I set it to it quits and goes back to 800 x 600.

---

### Post by Qwerty_ on 2007-10-21
Hmm I dont know but maybe this will help

```
sudo dpkg-reconfigure xserver-xorg
```

Also take a look here

[http://ubuntuforums.org/showthread.php?t=584561](http://ubuntuforums.org/showthread.php?t=584561)

---

### Post by DrQuincy on 2007-10-23
Thanks, I've done that loads of times, probably over 25 now!

I've even tried apt-get install --reinstall xserver-xorg

---

### Post by Tom Mann on 2007-11-02
How much RAM does the GFX card have? Make? Model?

---

