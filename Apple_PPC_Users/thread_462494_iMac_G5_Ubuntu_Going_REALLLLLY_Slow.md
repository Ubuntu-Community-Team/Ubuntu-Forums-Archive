---
title: "iMac G5 Ubuntu Going REALLLLLY Slow"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by miyamotofreak on 2007-06-02
So I installed Feisty Fawn (I'm pretty sure install was succesful). Ubuntu is going REALLY slow. Extremely slow. At least 8x slower than the livecd that I installed it with. I don't really know what's the problem. Also during the boot when I decide whether to use Ubuntu or OS X by pressing Alt the fans go nuts. Also I get a error message about the Ubuntu Settings Daemon (apparently it won’t respond). My computer is a iMac G5 1.86 GHz with 512 mb of Apple RAM and 1 gig of additional 3rd part ram (that worked fine with OS X). Other than it is the normal 17 inch model (pre-iSight). It can't respond or something. and by slow, I mean it takes forever to boot, the mouse moves at a frame every 2 seconds (so if I move it it appears 2 seconds later in different spot), typing is slow (I ain't a fast typer but it can't keep up), just clicking any part of the desktop takes forever for it to open. The last thing to note is that the splash screen (that’s what I’m guessing it is) after shutting down the ubuntu livecd after the install goes nuts and all staticky (forcing me to turn it off by power button).  It does this when shutting down the installed version but it ends after a minute (so I don’t need to shut it down by power button). Any help is greatly appreciated.
PS: I did try a reinstall. Same persisting problems.

---

### Post by stmiller on 2007-06-02
The G5 machines require a 64bit install. At the installer boot prompt you have to press TAB to see options, and choose the powerpc64 option.

 Can you give me the output of

uname -a

?


And edit the xorg.conf file like this:

sudo gedit /etc/X11/xorg.conf

and comment out the line that says

Load  "dri"

so it then looks like

#Load  "dri"

This will disable some 3D for now, but that will also tell us if it's the ATI driver causing problems.

---

### Post by Auria on 2007-06-02
stmiller forgot to say it, but you most likely need to reboot after editing the file he mentionned

---

### Post by miyamotofreak on 2007-06-03
the uname -a output is:
Linux nawid-desktop 2.6.20-15-powerpc64-smp #3 SMP Sun Apr 15 06:52:37 UTC 2007 ppc64 GNU/Linux

working on the rest as we speak

---

### Post by miyamotofreak on 2007-06-03
Alright the Load Dri stuff didn't fix anything. Should I change it back?
EDIT: Nevermind the splash screen at the end is now fixed. Speed still is same.

---

### Post by stmiller on 2007-06-03
Okay that is the correct kernel. So the 64bit version did install okay. This is most likely a video driver problem.

Edit the file /etc/X11/xorg.conf   again and make these changes in the Device section:

```

Section "Device"

	Driver		"fbdev"

	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"

```

Then save, and hit Contrl+Alt+[delete key] to restart X to see the changes.

If yours is [this model]("http://www.apple-history.com/?page=gallery&model=imac_g5_mid_05&performa=off&sort=date&order=ASC") then it is ati. If it was the previous iMac G5, then you need to specify

Driver    "nv"

The ideal driver for the ATI iMac G5 is

Driver "radeon"

though this may be causing problems for some reason.

---

### Post by miyamotofreak on 2007-06-03
Okay before I changed it, it was like this


> Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:240:16:0"
	Option		"UseFBDev"		"true"
EndSection


Now it's like this with no improvement. What changes should I make?

> Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fbdev"
	BusID		"PCI:240:16:0"
	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"
EndSection

---

### Post by cerbero on 2007-06-03
I just want to say that I have this exact same problem, with the exact same iMac model, as we speak. I also have the powerpc64 kernel installed, and the mouse moves at about 0.5 frames/sec. If anyone has seen this before and has a solution, I'd be immensely grateful.

BTW, load averages (from `uptime`) is something like "6.x 4.x 5.x" if i login to another tty and check it.

---

### Post by stmiller on 2007-06-03
And you restarted X after making those changes?

This framebuffer driver should work without any fuss. Hmmm...

If you can get to a terminal and type

top

and enter, you can see what is slamming the CPU perhaps. If it says Xorg or X with 99% CPU or something like that, then we know it's a video problem for sure. If not, then maybe some other running process is going wrong.

---

### Post by miyamotofreak on 2007-06-03
I rebooted again and now it's going at a good speed! Xorg is taking about 5% CPU. Is there any check I can do to make sure my Radeon 9600 (and other components) will work?
UPDATE: Nevermind the problems continue. It's from a process I think called mouseemu or emumouse

---

### Post by cerbero on 2007-06-03
@miyamotofreak: Glad to hear it - guess there's some hope for me aswell :) Was that after making all the changes proposed in this thread, or did you reset the settings before this reboot?

*Edit:*
Ok, back after a reboot. For me, the problem was mouseemu, which was taking up almost 100% of the CPU. Once I killed mouseemu, everything just flies. Is it safe to completely remove mouseemu, or do I need it for anything? (I don't use an Apple mouse, but a 3rd party, multiple-button one).

Now on to getting "true" 24 bit colors.

---

### Post by stmiller on 2007-06-03
Hey great glad you found a fix. You should change the driver part of your xorg.conf to

Driver "radeon"

to use the radeon driver. 3D is somewhat buggy for some in PPC Linux, but the radeon driver seems to work fine for most Radeon cards.

The make sure Default Depth is set to 24 for 24bit color, like this:

```
Section "Screen"

        DefaultDepth    24

```

---

### Post by miyamotofreak on 2007-06-03
How do you completely delete the mouseemu process so I never see it again?

---

### Post by cerbero on 2007-06-04
> **miyamotofreak said:**
> How do you completely delete the mouseemu process so I never see it again?

I simply uninstalled it using apt:

```
apt-get remove mouseemu
```

(Could be done through Synaptic too, I guess).

---

### Post by aantn on 2007-09-15
> **stmiller said:**
> The G5 machines require a 64bit install. At the installer boot prompt you have to press TAB to see options, and choose the powerpc64 option.

What? The iMac G5 isn't a 64 bit machine. I've been using the regular version. Should I be using something else?

---

### Post by silbro on 2007-09-15
Hey,

This is exactly the problem I had with the same iMac :) thx guys!

---

