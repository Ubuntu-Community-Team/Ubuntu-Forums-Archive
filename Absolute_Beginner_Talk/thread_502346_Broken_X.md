---
title: "Broken X"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Ink-Jet on 2007-07-16
Whilst trying to install Beryl (following [[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html]("this guide"), I somehow managed to break X.

I ran the command 
```
sudo apt-get install nvidia-glx
```
and then re-started X, missing out the following command.
After logging back in, I realised my mistake, and ran the command
```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```
and re-started X again.

The system now boots fine, and I can get to a CLI, but I am greeted with this message a few seconds after getting to the command line.

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes >        <No>"

Yes gives me a lot of information, and at the bottom "Fatal sever error: no screens found"
It then goes on to a more detailed view, that I can't make heads or tails of.
It then returns me to the command line.
This entire process is somewhat, messy. Srange lettering around, etc.

I am running Ubuntu 7.04, some Intel graphics card, if I remember.

I'm assuming it has something to do with a new xorg.conf or something, but I've never done anything like this before.

Anyone know how to fix the problem?

---

### Post by phr0ze on 2007-07-16
Post your /etc/X11/xorg.conf file. We can at least get your X working again. (probably by changing your graphics driver back to "nv".)

---

### Post by twiceasworn on 2007-07-16
Did you back up your xorg.conf before you changed it?  If you did, then just rename the backup to xorg.conf and reboot and you should be back in business.  If you didn't, then do a ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CautionaryX on 2007-07-16
It wasn't a good idea to install an nvidia driver for an intel based graphics card (if you indeed have an Intel graphics chip). The nvidia drivers are what most likely broke your X. 

You'll have to uninstall the nvidia driver too.

---

