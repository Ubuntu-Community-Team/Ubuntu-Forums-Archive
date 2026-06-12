---
title: "Screensaver and configure desktop crash"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by buntu_hugenewbie11 on 2007-04-15
So I recently updated and upgraded everything but now when I try and configure my desktop kde crashes and restarts. As well when my screensaver turns on kde crashes. As well when I go to control center and try to adjust screen saver it crashes. There's some terminal code that I can't read because it goes by too quickly (something about a warranty).
Could this be that I just need to reinstall my nvidia driver or something?
Or is there something else I should try.
Please help me.
Crashing is usually just a microsoft event :-(

---

### Post by Tundro Walker on 2007-04-15
I had a similar experience with the screensavers, and in my case it was trying to set an OpenGL-based screensaver in KDE when the OpenGL library (can't recall it's name off-hand) in Edgy 6.10 didn't support my graphics card (which was an old Matrox dual-head G450).  Not only were OpenGL screensavers borked up, but I couldn't run any OpenGL 3d software (games, compiz, etc).  It appears other have similar problems with anything 3d/OpenGL and screensaver-oriented if it causes over-heating and such...

[http://ubuntuforums.org/showthread.php?t=405495](http://ubuntuforums.org/showthread.php?t=405495)
[B]
Switch off Screensaver via Terminal...[/B]

The responder to that post suggested using the following in terminal to switch off your screensaver.

```
xset -s off
```The "xset" command lets you set your X window options from command-line.  The -s switch lets you set screensaver options, using various flags.  Read the "man xset" for further details.  With the screensaver switched off, you should (theoretically) be able to open up the GUI screensaver window, and it'll be switched off there, too.  Then, before activating it, select a non-OpenGL screensaver.

**Check Log Files...**

X/K/Ubuntu, by default, is set to log quite a bit of stuff while it's running.  You coud try digging through your home directory's ".xsession-errors" file to see if it logged any errors.  If that doesn't reveal anything, try looking at the various log files in "/var/log".  The "Xorg.0.log" file may reveal something pooping out on you.

**Get rid of Screensavers (*pout*)...**

If worse comes to worse, you can open up Synaptic or Adept and uninstall your screensaver.  Screensavers don't really "save" the screen these days, they're mostly just for show, and still keep the monitor on, wasting power.  I personally don't use a screensaver...I just have the Ubuntu Power Manager (System > Preferences > Power Management) blank my screen after 10 min.

As a side note, you can install a package called "brightside", which enables screen-edge actions.  You can use it to mouse-over to a corner and instantly switch your monitor into Standby or Suspend mode if you're going to be away for a while.  Aside from using it as an insta-screensaver, you can modify the actions of brightside to do other things when you mouse onto an edge or corner.  EG: default edges let you jump from one workspace to another, but you can configure it so when you mouse into a corner or edge, and application starts, a script runs, etc.  Pretty cool!

---

### Post by buntu_hugenewbie11 on 2007-04-15
Ok you're right, it has to do with anytime the opengl stuff is needed. So it is no longer a screensaver issue.
It crashes even as I check my openGl info in the nividia X application. :-(
Or when I open up a game that needs opengl ppracer.
so turning off scrensaver is not the solution. :-(
What sucks is that everything was working fine yesterday.
Should I reinstall my vid card? 
If so how??
argh :-(

---

### Post by Tundro Walker on 2007-04-15
You say it was working fine yesterday, then borked up today.  So, did you run an update or something between that time?

EG: I was messing around with my NVIDIA settings to get my screen to look pretty, colorful and vibrant.  I found out I could use "nvidia-settings --load-config-only" to get my config to auto-load, but it still wouldn't (the settings GUI would still pop-up, forcing me to close it).  So, I looked online for some advice, and followed some guys procedure for running nvidia-xconfig.  It backed up and replaced an xorg file, and afterwards my machine will kinda slow to boot up the Gnome GUI (and still loaded the stupid Nvidia settings GUI...d'oh!).  So, I retraced my steps, bumped off the xorg file it made and replaced it with the backup...problem solved (well, the Gnome GUI boots up quickly again, but still the stupid Nvidia settings GUI loads, too...blech!)

Ok, my personal story aside, did you try something with your video card?  Did you mess with any settings?  Did you use Automatix to install drivers for it, and perhaps when your system updated, it broke the libraries somehow?

If you used Automatix, or EasyUbuntu, you could try uninstalling the Nvidia drivers from those respective applications, then reinstall them from them.  (I used Automatix2 to get my Nvidia up and running, and it's been ok, even with system updates.  I think they tweaked it to better handle system updates.)

SIDE NOTE...

Try posting any error messages you get from log files or such.  EG: try opening a terminal and running the following...

```
tremulous > /home/*(your home folder)*/Desktop/t.txt 2>&1
```Replace **(your home folder)** with the actual name of your home folder, and replace **"tremulous"** with whatever 3d game you're going to test with (IE: one that crashes).  The ">" will pipe the terminal feedback into the "t.txt" text file in your "/home/<your home folder>/Desktop" folder.  The "2>&1" tells it to pipe the "stdout" and "stderr", so you not only log what went right, but what went wrong, too.

Post what the t.txt log file says, and folks with more techno-savvy then I have should be able to help you...

---

### Post by buntu_hugenewbie11 on 2007-04-16
Turns_out I had to reinstall the NVIDIA drivers- I used the script from link below along with coolbits and it runs sweet now.
Thanks though.
[http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+driver+restart+fails](http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+driver+restart+fails)

---

