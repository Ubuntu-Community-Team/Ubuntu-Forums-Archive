---
title: "Help me fix my ATI card pls...."
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by mike23 on 2007-12-23
Hey all.. thanx in advance for any help....
I had an nvidia 8600 gt card and decided to swap it for an ATI 1950pro...
I have ubuntu 7.10 and dual boot xp(only for games such as nfs pro and crysis)..
When i booted ubuntu for the first time after swaping cards, ubuntu by itself removed the nvidia drivers and installed ati.. after system restart, and the ubuntu thing while booting i get a black screen but the monitor is still swiched on (not power save).. And nothing happens...
Can anyone help?? 
Thanks....

---

### Post by erfahren on 2007-12-23
you could try this:
boot into recovery mode from the GRUB menu. after it does its thing booting you'll be prompted to enter the root password, enter your user password. you should get the root prompt ( # ).

enter 
```

dpkg-reconfigure xserver-xorg

```
you can just select the defaults for most of the settings. When you get the part about the driver you should actually want the "ati" one. The basic, default driver that xserver uses is "vesa" and it might be the one it's trying to load. The driver named "ati" is the open-source driver for ATI cards and should work better. (the proprietary ATI driver is called "fglrx", which you wouldn't have installed yet).

(it automatically creates a backup of your /etc/X11/xorg.conf file before it starts.)

to reboot, from the command prompt type 
```

shutdown -r now

```
(shutdown reboot now)

note: I've never actually used that (in recovery mode) before so I can't really tell you any more of what to expect. It should help though. 

the back up copy it makes is named strangely, like "xorg.conf.xxxxxxx" ("x" is a series of numbers).
if you want to create your own just do
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back1

```
(or whatever you name it) - no need for "sudo" since you'd be logged in as root (so be careful).

to list the files in the /etc/X11 directory
cd into it and ls ("list")

- hope that does the trick

---

### Post by mike23 on 2008-01-11
sorry...... tried it out but didnt help:(

---

### Post by Sef on 2008-01-11
Do you have a Live CD?  If so, run it and see if you can boot up ok.

---

