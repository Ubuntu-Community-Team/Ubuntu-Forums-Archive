---
title: "Video driver/black screen help!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by radioraheem8 on 2007-08-29
Hi everyone, newbie here who has been playing with ubuntu for the past week.  I had everything going well until last night, when my video drivers seemingly failed (oddly, my GUI had fuzzy vertical lines running down the screen, but I had been trying to figure out how to fix that).  So I was booted to the command prompt only, which for me, is the bowel of hell.  Close to clueless in that interface, though I had been practicing on terminal, I'm afraid of doing more harm than good.  

So my problem.  Last night I tried to run something along the lines of sudo apt-get install xorg/yada yada -intel (my video card).  Now I'm getting the black screen after that install completed.  I fear that I had created this problem long ago when I was installing ubuntu, trying any commands I came across that had to do with video devices, creating possible conflicts.  

Another problem is that I am unable to copy and paste my CPU info here as I am typing this on my PS3, as I no longer have viable internet access via my PC.  I typed the lspci command, and found that my video driver is an Intel 820-something.  Yes, an old piece of junk, but I wanted to try ubuntu on an older device.  I searched this site and found a link to a wiki page that said that driver is only supported up to the version before mine (feisty fawn).  Could that be a problem?

Any help on how I can fix this issue using command prompt only?  Or am I so far gone that I should wipe everything and restart from scratch?  Is Feisty Fawn too much for my Compaq EN to handle?  

Any help is much appreciated.  Thanks!

---

### Post by benerivo on 2007-08-29
You could try running this command and selecting the default options unless you definitely know differently... ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by radioraheem8 on 2007-08-29
> **benerivo said:**
> You could try running this command and selecting the default options unless you definitely know differently... ```
sudo dpkg-reconfigure xserver-xorg
```

Okay, since I had the black screen at bootup, I used my Ubuntu Desktop disk to boot from.  I tried that command and got this message (after entering the default values):

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070830000341

I think I had run this app previously, but that it had locked up on me or something.  Any ideas?

---

### Post by w4ett on 2007-08-29
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "intel" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

---

### Post by radioraheem8 on 2007-08-30
> **w4ett said:**
> From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "intel" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

Ok, this probably sounds stupid, but how do I stop the GUI from starting up?  That is, getting into the command prompt only?  Because now my CPU starts up the desktop GUI, but then only a black screen comes up...also, how much KB should I allocate in that xserver menu?  I read somewhere that 8 megs was good; since it's blank, there's no default value.  Suggestions?  

Thanks for all the help so far!

---

### Post by w4ett on 2007-08-30
> **radioraheem8 said:**
> Ok, this probably sounds stupid, but how do I stop the GUI from starting up?  That is, getting into the command prompt only?  Because now my CPU starts up the desktop GUI, but then only a black screen comes up...also, how much KB should I allocate in that xserver menu?  I read somewhere that 8 megs was good; since it's blank, there's no default value.  Suggestions?  

Thanks for all the help so far!

From the Grub boot menu select "recovery" mode.....leave the memory blank....let X control the memory allocation automatically in conjunction with what is allocated in bios as shared memory...

---

### Post by radioraheem8 on 2007-08-30
Thanks a lot man, that solved my video problems!  Even better, the fuzzy red lines have vanished!  Oddly though, all of my old computer settings are gone, like bookmarks, programs, etc.  Nothing big, just curious as to why...

---

### Post by w4ett on 2007-08-30
Reboot and your original settings will be there.

---

