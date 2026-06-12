---
title: "Mugen hates me."
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by SMA11784 on 2008-01-29
Alright, plan A was to run Winmugen using Wine.  I copied all the relevant files and folders to .wine/drive_c/ and made a launcher.  I click the launcher and I get a popup;

Error message: Can't open data/mugen.cfg. Make sure you have
extracted with directories
Error reading data/mugen.cfg

There is indeed a file named "mugen.cfg" in .wine/drive_c/MUGEN/data but for whatever reason, Winmugen or wine or Winmugen in wine just can't see it.

Plan B, get the Linux version.  It's a tar.bz2 from randomselect.  I right click, Extract Here, everything in the folder looks kosher, I double click and nothing happens.  I right click and Open, nothing happens.

I took the advice in [this thread](http://ubuntuforums.org/showthread.php?t=581230) and killed AppArmor.  Mugen runs, but windowed.  If I set it to run fullscreen in mugen.cfg, it does nothing.

I would prefer to get WinMugen running so that the characters I make and use will be compatible with my friends who are pretty much all running WIndows.  Any suggestions are welcome.

---

### Post by skymera on 2008-01-29
do you have the installer?

without that there are no registry entries so the program dosent know where it is or where anuthing else is.

ge the installer and install to your wine dir.

---

### Post by SMA11784 on 2008-01-30
It doesn't have an installer.  The compiled exe is just sitting in the archive.

[http://unofficial-winmugen.jpn.org/](http://unofficial-winmugen.jpn.org/)

---

### Post by jan quark on 2008-01-30
the basic procedure to compile source packages like it seems the mugen tar is
is to navigate to the extracted folder in the terminal using cd / change directory

then applying this three step code
./configure
make
make install

you need the build-essential packages to compile applications these can be installed via the synaptic package manager just type into the search field build-essentials

---

### Post by SMA11784 on 2008-01-30
You guys aren't actually reading my problem, are you.  You're just skimming for keywords and spitting out FAQ answers.

I have build-essentials.  Linux Mugen is already compiled installed and works when I kill AppArmor, it just won't fullscreen.  That's not the problem.  Nor is the problem that Winmugen won't run in wine; it runs, but for some reason it can't find 'mugen.cfg' even though it's in the correct subfolder.  I was able to replicate the error message on a Windows machine by simply renaming 'mugen.cfg' and trying to run Winmugen.

Winmugen does not rely on registry values of any kind.

---

### Post by thrasher6900 on 2008-02-09
I'm having the same problem.  However at one point in time(I think in between plugin and patches where added) Pressing alt enter would make you have a full screen


So I hope that this bumps up so we can both gain some knowledge lol

---

### Post by amoore on 2008-03-22
same problem here! I really wish I could get fullscreen mode to work. In my mugen config if I set fullscreen = 1 then Mugen just crashes.

---

### Post by Sirellyn on 2008-06-25
Same problem here as well.  This is what it specifically says though:

(If I try to run it from a terminal window)
```
Loading button config for P1 joystick.
Loading button config for P2 joystick.
Initializing keyboard.
Initializing sound...no midi device found.
Initializing graphics.
Segmentation fault
```


(This is what happens if I try to run it from a full screen console)
```
Loading button config for P1 joystick.
Loading button config for P2 joystick.
Initializing keyboard.
Initializing sound...no midi device found.
Initializing graphics.
Library (built in) message: Can't change video mode.

Error Detected
```

I can't find any responses on the mugen site.  My only ideas are:

- Change the terminal text mode to match the video mode mode so it doesn't have to change.  The ways I've read to do this so far seem very hacky though.

- Don't actually run outside a window but "fake it" by turning desktop resolution down, getting rid of task tray, running window without the border etc.  This also seems like a very bad way of doing things.

Thats the best I've got for now. :-(

---

### Post by Sirellyn on 2008-06-29
FOUND IT!

You DO need to run your console session in the exact same screen resolution and depth as what you are trying to play fullscreen (in Linux).  It even says so in the readme file:

- Linux version is new. There are several known problems at this time:
  - depth in mugen.cfg must match depth when in X
  - console must use same res and depth as screen. Not allowed to switch
    res/depth in console (unless root)

So how do you do this?

Well I found the answer on this page:
ivapinkfloyd.blogspot.com/2008/06/how-to-change-console-resolution.html

To summarize;

To change the resolution and colour depth of the console you need to edit the **/boot/grub/menu.lst** file and add one parameter to the line containing the kernel to boot. On a Debian Lenny system, this should look something like:

title Debian GNU/Linux, kernel 2.6.24-1-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-1-686 root=/dev/hda1 ro quiet [COLOR="Red"]**vga=785**[/COLOR]
initrd /boot/initrd.img-2.6.24-1-686

The new parameter added is vga=785 **(NOTE: This is a different number than the web page link!!!)**, which means a resolution of 640x480 with a colour depth of 16 bits per pixel (65,536 colours). 

You can also set Stretched = 1  in the mugen.cfg file to make sure it really does run full screen.

When you reboot your system, and press Ctrl+Alt+F1  then log in, you should now be able to run mugen from the command prompt.  

(If you are still having troubles, try running it with sudo or log in as root with su)

---

