---
title: "Out of range resolution"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by eljoeb on 2007-07-01
Hi everyone,

I just installed Ubuntu today (dual boot with xp for now), and I did something stupid.  WHen it asked me what resolutions my monitor could take, i just pressed enter on the one i wanted, which seems to not check anything.  Installation went okay, but now that I'm booting into the system, the screen starts spazzing and says its out of range.  

I have an Nvidia graphics card.

What's going on and how can I fix it?  Please ask for any other details you may need.

Thank you in advance,

Joe

---

### Post by brooksbp on 2007-07-01
Sounds like your Xorg configuration file is messed up.  You probably will have to do the following:

1) Login to your machine w/o a GUI. (press Ctrl + Alt + F4 to get to another login screen & login...)
2) Edit your xorg.conf file to support native resolution. (run the cmd: 'sudo vi /etc/X11/xorg.conf' scroll down till you see a listing of resolutions and make sure you have native ones listed. feel free to remove non-native resolutions.)
2) Edit your xorg.conf file to run on native nvidia driver support. (use the commands above and when you see 'Device' driver make sure it says "nv" not "nvidia" or anything else.)
3) Save.
4) Start GDM. ('sudo /etc/init.d/gdm stop/start/restart')

---

### Post by eljoeb on 2007-07-01
Thank you for your quick response.  I did what you said (bring up xorg.conf) but it seems that the driver is already set at "nv".  THe resolutions all look okay too, but the default depth seems strange (24).  I would imagine I want this at 16 or 32.  How exactly do I edit the xorg.conf file?  I tried typing in there but it wasn't cooperating.

Thanks

---

### Post by John.Michael.Kane on 2007-07-01
Either of these should get you going. 

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716")

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by wak_wak on 2007-07-01
Get to a command prompt boot & Alt F4)

At the prompt type:  sudo dpkg-configure xserver-xorg

You'll see some drivers come up.  Choose nvidia

When it gets to the resolution choose the appropriate one.

For all the rest just choose the defaults.

That should work.

---

### Post by regomodo on 2007-07-01
> **wak_wak said:**
> Get to a command prompt boot & Alt F4)

At the prompt type:  sudo dpkg-configure xserver-xorg

You'll see some drivers come up.  Choose nvidia

When it gets to the resolution choose the appropriate one.

For all the rest just choose the defaults.

That should work.

"get to a command boot prompt" means press ctrl+alt+f1. then log in

---

### Post by rocknrolf77 on 2007-07-01
Did you install the driver for your nvidia card? You can do that by going to System > administration > restricted driver manager :)

And it's enough with ```
sudo dpkg-reconfigure -phigh xserver-org
```

You can do that in "gui" too. Just hit ctrl - alt - bckspace to restart the gui (xserver)

---

### Post by regomodo on 2007-07-01
> **rocknrolf77 said:**
> Did you install the driver for your nvidia card? You can do that by going to System > administration > restricted driver manager :)

And it's enough with ```
sudo dpkg-reconfigure -phigh xserver-org
```

You can do that in "gui" too. Just hit ctrl - alt - bckspace to restart the gui (xserver)

i'm pretty sure that'll give you the usual crazy xserver errors with the option to the see logfile. easier just to use th cli

---

### Post by eljoeb on 2007-07-01
sudo dpkg-configure xserver-xorg is just giving me an error.  I can add "vga=791" to the boot command (don't know the terminology) and it gives me a really scrunched view.  So scrunched its got weird lines across it.  Maybe I can change 791 to something else (for 1280x1024) and it might be okay.  But how?

OR maybe the refresh rate should be changed.  Not sure how there either.

Changing the 24 to 16 didn't work either.  Getting frustrated... WIndows isn't supposed to be working better!

Okay, seriously.  Maybe I can turn off the nvidia driver and start up without them?  Could that be done?

Thank you for your answers

---

### Post by Raineer on 2007-07-01
> sudo dpkg-configure xserver-xorg is just giving me an error.

You should probably expand on this a little more, dpkg-configure **really** should work as it's a very basic tool and a great one to recover from display problems.

---

### Post by eljoeb on 2007-07-01
Uhhh... it works.  I think I typed it in wrong. Sorry.  It still isn't displaying right.  It looks like a very distorted login screen right now.

I have an NVIDIA 6600 gt... any known problems with it?

Thanks

---

### Post by eljoeb on 2007-07-01
Yay! I'm in!  I had to take that "quiet" boot command off and add "vga=794"

Only problem now is... I can't see my mouse pointer? Does this usually happen?  I went into pointer settings and noticed the default was blank.  I changed it but can't see my pointer.  I'm not starting another thread about this because I think it could be related to the nvidia driver.

Muchas Gracias

---

### Post by confused57 on 2007-07-01
> **eljoeb said:**
> Uhhh... it works.  I think I typed it in wrong. Sorry.  It still isn't displaying right.  It looks like a very distorted login screen right now.

I have an NVIDIA 6600 gt... any known problems with it?

Thanks

You might want to try the "vesa" video driver...then in Ubuntu, this guide will help install "nvidia" driver for your card:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

### Post by eljoeb on 2007-07-01
VESA did it! 

Thank you everyone!

---

### Post by Raineer on 2007-07-01
I'm glad you got it working, but just so you know VESA is like the "fall-back" driver in the set. You won't have 3d acceleration and might not have the resolutions you want.  Now that you know what WILL work, when you get some free time you might play with getting the 'nv' driver to work and then finally the 'nvidia'

---

### Post by confused57 on 2007-07-01
> **eljoeb said:**
> VESA did it! 

Thank you everyone!
Glad it worked...you might want to make a backup of your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

Then try installing the nvidia driver, using the link that I gave you earlier...you'll actually be creating a backup of your xorg.conf by following the instructions.  These instructions are for Feisty, which I assume you're using.

It's mostly just copy & paste into a terminal, using the instructions for Method 1...

If you get an xserver error, "Ctrl+Alt+F1" to get to a console, then restore your backup:
```
sudo cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```

You'll get MUCH better performance with the nvidia driver for your video card....the link is pretty easy to follow(copy&paste)

---

### Post by rocknrolf77 on 2007-07-02
Have you tried ```
sudo nvidia-xconfig
```

The vesa drivers are really bad for using you computer. Everything will go really slowly.

---

