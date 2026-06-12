---
title: "Bizarre screen resolution fluke"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by northerndude81 on 2007-08-23
OK so when I installed Ubuntu the default resolution was whatever one step up from 1024 x 768 is (I can't remember exactly) but I lowered it to 1024 x 768 because it was easier for me to see.  Anyway, so I've been running without any problems on 1024 x 768 for about a week now, but then this morning I boot up the machine and bizarrely the resolution has jumped to 800 x 600.  I didn't change it, it just changed by itself while the machine was turned off over night, apparently.  So my questions are 1) how/why on earth did this happen? and 2) how can I get it back to 1024 x 768?  This seems really weird to me and I would appreciate any help.  Thanks.

---

### Post by rexy on 2007-08-23
try CTRL-ALT-SHIFT and - or + to cycle through different resolutions

---

### Post by northerndude81 on 2007-08-23
Oh I should mention that I've rebooted several times and it's still stuck in 800 x 600, and that also when I try to change the screen resolution the only options now available are 800 x 600 and 640 x 480.  1024 x 768 and the other higher resolution no longer appear in the menu.  How can I fix this?

---

### Post by northerndude81 on 2007-08-23
...And ctrl + alt + shift +/- only allows me to cycle between 800 x 600 and 640 x 480.

---

### Post by rexy on 2007-08-23
try sudo dpkg-reconfigure xserver-xorg

it tries to reconfigure your x
alternatively post your /etc/X11/xorg.conf and /var/log/Xorg.0.log

---

### Post by northerndude81 on 2007-08-23
As far as I can tell sudo dpkg-reconfigure xserver-xorg did nothing.  It asked me to choose a video driver or something so I did and that was it, but the problem didn't go away.

When I try  /etc/X11/xorg.conf and /var/log/Xorg.0.log they both tell me "permission denied," but I am the only user so I don't see how I can be denied.  What next?

---

### Post by Skillet98 on 2007-08-23
When it asks you to choose your video driver, try setting it to VESA.

---

### Post by northerndude81 on 2007-08-23
It is already set to Vesa.

---

### Post by rexy on 2007-08-23
you can read them using sudo, but the log should be publicly vieweable

---

### Post by northerndude81 on 2007-08-23
Yes well maybe it should be but it's not.  This is driving me crazy here, what can I do to return my resolution to 1024 x 768???

---

### Post by rexy on 2007-08-23
well you can access them with sudo at least, and then copy them and attach them to the post. Without those it is very hard to figure out why your resolution is set to max 800x600

---

### Post by northerndude81 on 2007-08-23
Sorry I don't understand what you mean by access them with sudo.  I am very new to Linux and Ubuntu.  Could you tell me the exact command to enter into the terminal to see them?  Then I'll post them.  Thanks.

---

### Post by rexy on 2007-08-23
new post

click on attachment

enter /etc/X11/xorg.conf and /var/log/Xorg.0.log in two seperate upload fields

hit upload

---

### Post by rexy on 2007-08-23
if uploading  files fails try using sudo cp /etc/X11/xorg.conf ~ this copy's it to your homedirectory

then chmod 777 ~/xorg.conf to make it readeable , then try uploading again, works the same for the Xorg.0.log

---

### Post by alienexplorers on 2007-08-23
Exactly what video card are you using and do you have the most current drivers?

---

### Post by A3sthetix on 2007-08-23
What kind of graphics card does your computer run? If it is an nVidia or ATI, you might need to install restricted drivers. Find out the gfx card model and look into that -- that usually solves my resolution issues.

---

### Post by A3sthetix on 2007-08-23
Looks like alienexplorers beat me to the punch.

*shakes fist*

---

### Post by northerndude81 on 2007-08-23
Yeah it's an nVidia graphics card, buy why would it be working fine yesterday but this morning when I turn on the machine it's messed up?  Anyway how would I check for the drivers?

---

### Post by A3sthetix on 2007-08-23
New updates might have been isntalled, causing something to revert to default settings. When I first installed ubuntu on my lappy, I could only get 1024 x 768. I have a widescreen, so this sucked.

What I did was installed Envy (helps install gfx drivers) and let the program do the rest. Before you do so, find out the exact model of your nVidia card (ie. GeForce Go 6150 in my case) and post it here. I'll give you a link to instructions if needed.

---

### Post by w4ett on 2007-08-23
Lets simplify this a bit and go back to the begining:

From the terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type <Ctrl><Alt><Backspace> to restart  X.

to view your xorg.conf file, from the terminal type:

```
cat /etc/X11/xorg.conf
```

copy and paste the results from the terminal to the forum.

---

### Post by northerndude81 on 2007-08-23
w4ett that solved the problem.  I still don't understand what went wrong to begin with but whatever it was you've fixed it for me.  THANK YOU.

---

### Post by w4ett on 2007-08-23
NP.....Now...to enable the restricted driver for your Nvidia card go to System>Administration>Restricted Driver Manager....Let the system install the appropriate proprietary driver for your card.  Tic the box to enable the driver, reboot and voila...you should be good to go.

If you encounter problems like xserver errors, do the:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and reset xorg.conf like before, then you can re-attempt the driver installation.

---

