---
title: "Changing xorg.conf"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by JBS on 2007-01-07
Hello.  I am new to Ubuntu, and don't really have any Unix/Linux experience either.  I have two monitors and was looking how to implement dual monitor support.  Using the root login from the desktop, I changed my xorg.conf file, but I made a mistake.  Now the desktop won't load, and when I try to change my xorg file from the console, I get a permission denied error.
After logging into recovery mode, what do I type to be able to change my xorg file?  Thank you.

---

### Post by slimdog360 on 2007-01-07
add a 'sudo' without the quotes in front of whatever you are trying to type.

---

### Post by Ben Sprinkle on 2007-01-07
```

sudo dpkg-reconfigure xorg-xserver

```
Is a terminal safe gui for re configuring your xorg.conf. ;)

---

### Post by aysiu on 2007-01-07
First of all, you don't need to boot into recovery mode to make root changes. Ubuntu uses this thing called *sudo* instead of root. When you have your Xorg file fixed, you can read about it more here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The easy way to fix your /etc/X11/xorg.conf file is to boot into regular (not recovery) mode, log in, and type ```
sudo dpkg-reconfigure xserver-xorg
``` enter your user (not root) password, and then answer the questions as best you can. If you don't know the answer, just go with the default. Finally, type ```
sudo /etc/init.d/gdm restart
``` and your graphical point-and-click interface should be up and running again.

---

### Post by MkfIbK7a on 2007-01-07
to do it with an easy to use gui questionaire do 
sudo dpkg-reconfigure xserver-xorg
answer the questions

---

### Post by MkfIbK7a on 2007-01-07
woah  2 people beat me to it...:D

---

### Post by Ripfox on 2007-01-07
It's 

sudo dpkg-reconfigure xserver-xorg

---

### Post by Ripfox on 2007-01-07
wow moving fast...heh

---

### Post by JBS on 2007-01-07
Wow, such fast replies.  Thanks.  Yeah, I saw the sudo dpkg-reconfigure xserver-xorg thing in Google, tried it, and it didn't work.  I think I left a space in between dpkg and -reconfigure, at least I'm guessing that was the problem.  Anyway, I'll restart my computer (dual boot), go back into Ubuntu, and try again.  Thanks.

---

### Post by bodhi.zazen on 2007-01-07
Once you fix X ....

Setting up dual monitors depends on what graphic card (s) you are using.

For example, with the latest nVidia driver you do not need to edit xorg.conf by hand as extensively any longer (at least i don't with my monitors). Adding information on my second monitor and confirming the Horiz and Vert refresh rates of both monitors .....

Much easier ....

The command is:```
nvidia-settings
```

If you can tell us your video cards we can direct you to links and help if you get stuck ...

Oh, and always make a backup of system files before you edit them. If needed you can then restore from backup ...```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

HTH 8)

---

### Post by JBS on 2007-01-07
Well, I was able to fix my problem, thank you everybody.
bodhi.zazen, my video card is a GeForce FX 5500 with dual monitor ports.

---

### Post by bodhi.zazen on 2007-01-07
Try these links:

[http://www.ubuntuforums.org/showthread.php?p=1773584](http://www.ubuntuforums.org/showthread.php?p=1773584)

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

---

