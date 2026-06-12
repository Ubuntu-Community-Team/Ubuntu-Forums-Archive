---
title: "Nvidia driver"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Benbow on 2008-02-07
I know that my graphics card is a Nvidia but I am not sure which one. I have been running Ultimate Edition (Ubuntu) which automatically installs the correct driver but I am now trying Hardy Heron (I know, it isn't released yet) and I am having huge success with it.
If someone can help me with these drivers I will be very grateful.

---

### Post by PmDematagoda on 2008-02-07
What Nvidia VGA card are you using?

---

### Post by taurus on 2008-02-07
Open a terminal and run

```
lspci
```

---

### Post by AndreiMe on 2008-02-07
interesting :-?

---

### Post by Benbow on 2008-02-07
Thanks for your swift response. The card is Nvidia GeForce 7300 LE and the Nvidia site tells me that they don't support it - I know they do as Ultimate Edition has recognised it and installed it several times!
I really would like to continue using Hardy Heron as I find that I am learning more and am able to pass on what I learn.
Any ideas where I should look for this driver?

---

### Post by taurus on 2008-02-07
Have you looked in System -> Administration -> Restricted Drivers Manager to see if there is a driver for your graphic card?

---

### Post by Redenbacher on 2008-02-07
I just went to the Nvidia site and your card is supported. Your drivers fall under GeForce 7 series for Linux
This link will take you to the site for the linux 32 bit drivers for GeForce 7 series:
[http://www.nvidia.com/object/linux_display_ia32_169.09.html](http://www.nvidia.com/object/linux_display_ia32_169.09.html)

---

### Post by SOULRiDER on 2008-02-07
You need the nvidia-glx-new package, note the -new at the end.

---

### Post by Benbow on 2008-02-07
I must have poor sight! You are right it is there. Unfortunately in the process of looking for the driver, I clicked on screens and graphics, then on test and my desktop promptly disappeared!! I knew I was pushing my luck when I commented that I was getting on well with Hardy!
Any ideas how I can get my desktop back?

---

### Post by FreakTech on 2008-02-07
I have the same griphics card and I am currently testing 8.04.  The restricted driver manager recognizes it and installs the correct driver perfectly.

---

### Post by taurus on 2008-02-07
What happens if you press <Ctrl><Alt>Backspace to restart X server?  Otherwise, get to another console with <Ctrl><Alt>F2 and reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by RSLxH on 2008-02-07
> **Benbow said:**
> I know that my graphics card is a Nvidia but I am not sure which one. I have been running Ultimate Edition (Ubuntu) which automatically installs the correct driver but I am now trying Hardy Heron (I know, it isn't released yet) and I am having huge success with it.
If someone can help me with these drivers I will be very grateful.

The restricted driver manager will install Nvidia now, with 3D acceleration. I did it last night after a quick reinstall.

Or if you want to try another way:
[http://forum.linux-hardcore.com/index.php/topic,1368.0.html](http://forum.linux-hardcore.com/index.php/topic,1368.0.html)

---

### Post by Benbow on 2008-02-07
Desktop still a problem. When I run
sudo dpkg-reconfigure -phigh xserver-xorg

Iget
benbow@benbow-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080207152306

Talk about opening a can of worms

---

### Post by taurus on 2008-02-07
> **Benbow said:**
> Desktop still a problem. When I run
sudo dpkg-reconfigure -phigh xserver-xorg

Iget
benbow@benbow-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080207152306

Talk about opening a can of worms

And what's wrong with that message?  It told you that it made a backup of your previous /etc/X11/xorg.conf to /etc/X11/xorg.conf.20080207152306.  Have you restarted your X server again after you reconfigured it?

<Ctrl><Alt>Backspace

---

### Post by Benbow on 2008-02-07
Sorry but this is beginning to get way above me!
I have restarted x server and restarted ubuntu. Something is wrong somewhere.

---

