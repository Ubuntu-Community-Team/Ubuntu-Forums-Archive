---
title: "Programs not ending up on my Appliactions button."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-08-04
Ok, so there has been quite a few times that I have installed a program and then I go to use them and they are no where to be found on the Applications button under any of the folders.

Take "FCEU" that I just installed. I was looking forward to some sweet NES action and it said everything installed perfectly but it's not on my Applications button anywhere.

Any ideas?

---

### Post by forestpixie on 2007-08-04
if the install doesn't specify a menu  - you won't get one.

Easiest thing to do would be make a launcher - right click desktop - browse for command - look in /usr/bin for  fceu

---

### Post by n.aggel on 2007-08-04
i am not sure it will solve your problems but try this:

go to System menu->Preferences->Main Menu and there  see if the installed programms are showing but are not ticked. If this is true tick them et voila, you will have them on your menu...

If not select {in the same dialog box} new item, and give the location of the program, plus a comment, plus an icon!

---

### Post by forestpixie on 2007-08-04
I've never seen that in there ! Just shows what can happen when you wander round with half open eyes:D

---

### Post by osc1882 on 2007-08-04
Ok, so I added it to my applications button. It was under Usr/games/fceu
And it's on my button now. But I click on it and nothing happens at all.
Any Ideas?

---

### Post by forestpixie on 2007-08-04
try running it from the terminal to see if it works from there

Edit - accessories > Terminal if you don't know :)

---

### Post by osc1882 on 2007-08-04
Hum, not really sure what you had in mind. I just cd'ed over to the older and typed the name of the program in. Here's the out put. I'm sure it's not what you had in mind.




grammatrain@tprb:~$ cd /
grammatrain@tprb:/$ cd usr
grammatrain@tprb:/usr$ cd games
grammatrain@tprb:/usr/games$ fceu

Starting FCE Ultra 0.98.12...

Usage is as follows:
fceu <options> filename

Options:
-xres   x       Set horizontal resolution to x for full screen mode.
-yres   x       Set vertical resolution to x for full screen mode.
-xscale(fs) x   Multiply width by x(Real numbers >0 with OpenGL, otherwise integers >0).
-yscale(fs) x   Multiply height by x(Real numbers >0 with OpenGL, otherwise integers >0).
-bpp(fs) x      Bits per pixel for SDL surface(and video mode in fs). 8, 16, 32.
-opengl x       Enable OpenGL support if x is 1.
-openglip x     Enable OpenGL linear interpolation if x is 1.
-doublebuf x
-special(fs) x  Specify special scaling filter.
-stretch(x/y) x Stretch to fill surface on x or y axis(fullscreen, only with OpenGL).
-efx(fs) x      Enable special effects.  Logically OR the following together:
                 1 = scanlines(for yscale>=2).
                 2 = TV blur(for bpp of 16 or 32).
-fs      x      Select full screen mode if x is non zero.
-connect s      Connect to server 's' for TCP/IP network play.
-netnick s      Set the nickname to use in network play.
-netgamekey s   Use key 's' to create a unique session for the game loaded.
-netpassword s  Password to use for connecting to the server.
-netlocalplayers x      Set the number of local players.
-netport x      Use TCP/IP port x for network play.
-cpalette x     Load a custom global palette from file x.
-ntsccol x      Emulate an NTSC's TV's colors.
                 0 = Disabled.
                 1 = Enabled.
-pal x          Emulate a PAL NES if x is 1.
-sound x        Sound.
                 0 = Disabled.
                 Otherwise, x = playback rate.
-soundvol x     Sound volume. x is an integral percentage value.
-soundq x       Sets sound quality.
                 0 = Low quality.
                 1 = High quality.
-inputx str     Select device mapped to virtual input port x(1-2).
                 str may be: none, gamepad, zapper, powerpada, powerpadb,
                             arkanoid
-fcexp str      Select Famicom expansion port device.
                 str may be: none, shadow, arkanoid, 4player, fkb
-inputcfg s     Configure virtual input device "s".
-nofs x         Disables Four-Score emulation if x is 1.
-gg x           Enable Game Genie emulation if x is 1.
-no8lim x       Disables the 8 sprites per scanline limitation.
                 0 = Limitation enabled.
                 1 = Limitation disabled.
-snapname x     Selects what type of file name snapshots will have.
                 0 = Numeric(0.png)
                 1 = File base and numeric(mario-0.png)
-nothrottle x   Disable artificial speed throttling if x is non-zero.
-clipsides x    Clip leftmost and rightmost 8 columns of pixels of video output.
                 0 = No clipping.
                 1 = Clipping.
-slstart x      Set the first drawn emulated scanline.  Valid values for x are
                0 through 239.
-slend x        Set the last drawn emulated scanline.  Valid values for x are
                0 through 239.
grammatrain@tprb:/usr/games$

---

### Post by forestpixie on 2007-08-04
you didn't have to cd to the directory - just open a terminal and then type fceu and enter

trying to see if it runs from the terminal, if not it could be that fceu isn't the right command to start it, eg oowriter from the terminal starts the Openoffice writeer program  

I don't know what the program actually is or does :)

if it doesn't run from terminal what is the output of 

```
ls /usr/bin/fceu*
```

---

### Post by forestpixie on 2007-08-04
Is fceu this

[http://fceultra.sourceforge.net/support.php](http://fceultra.sourceforge.net/support.php)

if so I've no idea - I don't actually do anything like that BUT
GFCEU is a GTK2 front-end - ie Gnome front end, I've done a search and it is in the repos

I don't know if it'll help, to install do this in terminal

```
sudo apt-get install gfceu
```

to remove it

```
sudo apt-get remove gfceu
```

---

### Post by osc1882 on 2007-08-04
Wow, I had no idea that this was a program with out a GUI. Now I know and thank you for pointing me in the right direction. I'm having a little bit of a problem with this gui, but this is not the place for that. Thank you once again.

---

### Post by forestpixie on 2007-08-04
whooah  too much beer - back 2morrow :)

---

### Post by forestpixie on 2007-08-04
competely unbalanced

---

### Post by osc1882 on 2007-08-04
lol

---

### Post by forestpixie on 2007-08-04
> **osc1882 said:**
> lol

:D ;)

Edit - it's all about what you listen too - Gong and REALLY REALLY old Genesis - old hippy I :completlyshot  -  a smiley that got missed!!!

---

