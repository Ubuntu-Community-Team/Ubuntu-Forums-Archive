---
title: "I Need Complete instructions for installation: PowerBook G3 Pismo 500 MHz"
date: 2009-09-25
forum: Apple Hardware Users
---

### Post by Firepowerforfreedom on 2009-09-25
I'm trying to install Hardy on a PowerBook G3 (affectionately referred to by all us used Mac guys [and anyone else who cares] as the Pismo). I've read about the video issues and have suffered them myself on the Live CD. I'm completely new at Linux (though I'm pretty experienced with Mac OS 9 and X, and Windows 95 thru Vista), so I need the complete, idiot-proof instructions on how to install it and fix the video issue. I've been able to use this Live CD with an iMac G4 (so I know it's good). I haven't tried to install with it yet, though.

Any help anyone can give would be appreciated.

---

### Post by gwydionwaters on 2009-09-25
this might be a good starting point
[http://ubuntuforums.org/showthread.php?t=1114297](http://ubuntuforums.org/showthread.php?t=1114297)

---

### Post by Firepowerforfreedom on 2009-09-26
That link would have been helpful under different circumstances. Thanks anyway.

OK, what I'm trying to do is install Ubuntu 8.04.1 Hardy Heron PPC from a standard Live CD onto my laptop. It has a video issue where it won't get into the X Window environment to install Ubuntu from the CD (the screen is filled with diagonal bars: a display setting problem). I've tried to change the settings using:

sudo nano /etc/X11/xorg.conf

However, nano won't let me save it. It says I don't have permission. Perhaps I can save it to my hard drive somehow, but I'm really, really, really new to Linux, and I don't know the directory of my hard drive. Somehow, I don't think it would help anyway unless I was booting from the HD.

I would really like to be able to install the thing using only open firmware or from Mac OS X, change the config file from outside the X Window environment (remember, I can't get into X Window until I change the config file), then boot back into X Window and sigh with relief and enjoyment.

Now, I want to dual boot (I'm a diehard Mac and won't give it up no matter what), so I've got my 120 GB (111 apparent) HD partitioned into 'Ubuntu', a 50-GB partition, and 'Mac OS X', a 61-GB partition. How do I install from openfirmware and change the config file without going into X Window?

HELP!!!!!

---

### Post by sweetleaf on 2009-09-27
> **Firepowerforfreedom said:**
> That link would have been helpful under different circumstances. Thanks anyway.
[...]
HELP!!!!!
Why exactly was the link unhelpful? I know that 8.04 != 9.04, and that iBook != Pismo, but I'd be surprised if *none* of the information in that thread applies. Complete instructions tailored to your precise situation may be hard to come by.

> **Firepowerforfreedom said:**
> OK, what I'm trying to do is install Ubuntu 8.04.1 Hardy Heron PPC from a standard Live CD onto my laptop. It has a video issue where it won't get into the X Window environment to install Ubuntu from the CD (the screen is filled with diagonal bars: a display setting problem). I've tried to change the settings using:

sudo nano /etc/X11/xorg.conf

However, nano won't let me save it. It says I don't have permission. 

I think the simplest workaround would be to try using the "alternate," non-graphical installer CD instead of the standard live CD. Remember to use a low speed when you burn it.

Otherwise, you could try dropping to single-user mode to edit xorg.conf. In that case you won't need sudo since you'll be logged in as root:

```
nano /etc/X11/xorg.conf
```

---

### Post by Firepowerforfreedom on 2009-10-01
OK. Sorry about not explaining. For starters, the iBook 500 MHz and the PowerBook G3 500 MHz are fairly similar, but they do have some glaring differences. The PowerBook is not recognized as having the right kind of monitor by Ubuntu (a problem the iBook doesn't seem to have). So I had to set it manually (it's sudo nano /etc/X11/xorg.conf, not nano sudo /etc/X11/xorg.conf, apparently), and presto: Ubuntu!
  I've learned more about Linux in these last two or three days than I have for my entire life. I'm fairly impressed with you Linux users, too! You guys are a shining example of how incredible things can be accomplished if we just learn to cooperate with one another. I'm planning on installing Xubuntu on my Pismo (I've gotten the instructions on how to dual boot a Mac, the right way, from another thread), and I will definitely be paying close attention to the Ubuntu community in the future.
  Based on the past 30 years of computer development, I will make a prediction:
  Within 20 years, Windows will either be Linux-based or it will be extinct.
  Within 20 years, Macintosh and Linux will be almost indistinguishable from one another.
  Within 20 years, 25% of all software will be open-source.
  
  I'm usually right about these things.

---

