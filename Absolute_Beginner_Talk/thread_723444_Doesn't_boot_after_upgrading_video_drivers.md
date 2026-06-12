---
title: "Doesn't boot after upgrading video drivers"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by JoshMcg on 2008-03-13
I installed ubuntu and it loaded fine but with a much lower resolution than it should have and it wouldn't let me correct it. Then it said I could use proprietary video drivers to enable 3d acceleration or something like that and when I installed those and restarted my computer it didn't boot. It had a black screen and I didn't hear the noises it usually makes when it loads the login screen. Right now I am running the live cd on the same system, and it is working just like it was before I installed the drivers, with a low resolution and my display is moved over about 1/4 inch to the right with a black bar on the left.

---

### Post by JoshMcg on 2008-03-13
My video card is onboard geforce4 mx.

---

### Post by jan quark on 2008-03-13
try to reconfigure the xserver

run in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by OffAxis on 2008-03-13
if it doesn't work with the -phigh switch (if it just kicks back out straightaway to the terminal and says it created a backup file)
run
```
sudo dpkg-reconfigure xserver-xorg
```

to run through all the xserver options, to set your monitor options, and to select your video driver. 'Vesa' is the generic one.

you can also use the liveCD to boot to a command line and try to start an x-server from there. When it errors out it'll print to the terminal.

---

### Post by JoshMcg on 2008-03-13
The proper resolution for my monitor is not an option in the configuration. The proper resolution is 1360x768.

---

### Post by JoshMcg on 2008-03-13
Also after doing that and restarting I cant even get into the terminal again. The livecd works fine though. 

edit - by "works fine" I mean it boots and things load but the resolution is really low

---

### Post by JoshMcg on 2008-03-13
I just copied the xorg.conf file from the live cd to the regular install and now it boots but my resolution is 800x600.

---

### Post by dokdoom on 2008-03-13
In your xorg.conf go down to the "Device" section. On the driver line what does it have when you are running the live cd. Whatever it says is what you want to use as the driver on your actual xorg.

---

### Post by JoshMcg on 2008-03-13
After I tried to update the drivers again and restarted the computer it boots with error message /etc/gdm/failsafexserer: line 47: [: too many arguments
warning: could not retrieve edid because get-edid is not installed

---

### Post by OffAxis on 2008-03-13
> The proper resolution for my monitor is not an option in the configuration. The proper resolution is 1360x768

Then pick something that you know will work (like 800x600), install the driver, and then manually edit the file.

```
sudo nano /etc/X11/xorg.conf
```

Find the Screen section, and in the Modes line add your resolution 1360x768
Restart x. (Ctrl+Alt+Backspace)

By the way, are you sure your video card can output to that resolution (at that color depth and that frequency)?

If it blinks out of existence you can reconfigure it again
```
sudo dpkg-reconfigure xserver-xorg
```

or replace your botched xorg with the backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

