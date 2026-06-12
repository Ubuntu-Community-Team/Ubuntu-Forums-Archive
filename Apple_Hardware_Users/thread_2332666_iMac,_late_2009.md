---
title: "iMac, late 2009"
date: 2016-08-02
forum: Apple Hardware Users
---

### Post by nickles1995 on 2016-08-02
Hello. I have an apple iMac from late 2009 with a radeon HD 4850 GPU, on to which I want to put at this point any linux. I have previously asked for help here: [http://www.forums.fedoraforum.org/showthread.php?t=309979](http://www.forums.fedoraforum.org/showthread.php?t=309979) however, no one has responded to the thread for a while so I doubt the problem is going to be solved. To reiterate the contents of the above, 
Whenever I boot from any linux disk, the screen shuts off immediately after grub. Starting fedora in basic graphics mode alleviated this problem, but the subsequent graphics performance was extremely poor and brightens adjustment didn't function, leading me to believe the GPU isn't being utilized at all. I was also unable to find any equivalent option in the grub menus of the ubuntu disks I tried. After googling, I found this bug, [https://bugs.freedesktop.org/show_bug.cgi?id=27314](https://bugs.freedesktop.org/show_bug.cgi?id=27314) which appears to be my problem. I also want to be able to run 64 bit VMs, because I don't have a 32 bit windows product key. if anyone here can do anything to help, or at least inform me that this is unequivocally a lost cause, it would be very much appreciated. Thank you.

---

### Post by QIII on 2016-08-02
Moved to Apple Hardware Users.

---

### Post by DigiAngel on 2016-08-03
Congratulations...you and I are in the same boat.  Look here:  [https://ubuntuforums.org/showthread.php?t=2332624]("https://ubuntuforums.org/showthread.php?t=2332624").  In a nutshell, it seems kernel v4 defaults to a different displayport...if you plug in an external monitor chances are on normal boot you'll get video on the external monitor.  I haven't found a solution yet to get it to work on the main screen...using dmidecode my iMac version is 9.1, with the exact same card as yours.  I run this devices pretty much headless 90% of the time so my /etc/default/grub.cfg contains:

```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=1"

```

which gives me nothing but a blank, lit screen.  After about 2 minutes DPMS kicks in and the screen powers off.  On times that I actually want to see the display I change my grub as follows:

```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0"

```

Which is most likely what you're getting when you boot into low res/safe-ish mode.  Good luck...I'll post to this or my post if I find a solution.

---

### Post by nickles1995 on 2016-08-04
> **DigiAngel said:**
> Congratulations...you and I are in the same boat.  Look here:  [https://ubuntuforums.org/showthread.php?t=2332624](https://ubuntuforums.org/showthread.php?t=2332624).  In a nutshell, it seems kernel v4 defaults to a different displayport...if you plug in an external monitor chances are on normal boot you'll get video on the external monitor.  I haven't found a solution yet to get it to work on the main screen...using dmidecode my iMac version is 9.1, with the exact same card as yours.  I run this devices pretty much headless 90% of the time so my /etc/default/grub.cfg contains:

```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=1"

```

which gives me nothing but a blank, lit screen.  After about 2 minutes DPMS kicks in and the screen powers off.  On times that I actually want to see the display I change my grub as follows:

```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0"

```

Which is most likely what you're getting when you boot into low res/safe-ish mode.  Good luck...I'll post to this or my post if I find a solution.

Well, you're obviously more knowledgeable about this than I am, but for what it's worth, I can confirm that radeon.modeset=0 produces the same results as basic graphics mode in fedora. In your linked thread, you said this worked in kernel v3? Is there any way I can just use that kernel, or is this an exceptionally stupid question?

---

### Post by DigiAngel on 2016-08-14
Yea I don't think kernel v3 is going to work with ubuntu 16.04.  I think we're kind of out of luck for now.

---

### Post by nickles1995 on 2016-08-14
> **DigiAngel said:**
> Yea I don't think kernel v3 is going to work with ubuntu 16.04.  I think we're kind of out of luck for now.
Damn. Thanks for trying, at the very least. Is there anything else I can do at this juncture, or am I out of luck? Would asking on other forums help, or is there anything I can do to try and get the bug fixed? I'm willing to part with $20 if there's anywhere that does anything like bounties for bugs.

---

### Post by entangled on 2016-08-15
If it is any help I have a mid-2010 iMac with radeon 4670 GPU. 
The only way I have found to make linux booters show on the main screen is to plug a 'dongle' into the mini displayport.
The dongle is a mini-displayport to VGA adapter with three small resistors plugged into the VGA end.
Looking at the VGA end of the adapter face on, with the wider part at the top, there are three rows of holes.
The resistors are plugged into the first three holes on the right of the top row and also into the first three holes of the middle row, no crossovers.
Use about 75 ohm resistors, but probably OK between 50 and 100.
This seems to force the main display to carry the video output.

Linux boots well and runs OK at the correct resolution but I think macOS is superior now.

---

### Post by nickles1995 on 2016-08-15
> **entangled said:**
> If it is any help I have a mid-2010 iMac with radeon 4670 GPU. 
The only way I have found to make linux booters show on the main screen is to plug a 'dongle' into the mini displayport.
The dongle is a mini-displayport to VGA adapter with three small resistors plugged into the VGA end.
Looking at the VGA end of the adapter face on, with the wider part at the top, there are three rows of holes.
The resistors are plugged into the first three holes on the right of the top row and also into the first three holes of the middle row, no crossovers.
Use about 75 ohm resistors, but probably OK between 50 and 100.
This seems to force the main display to carry the video output.

Linux boots well and runs OK at the correct resolution but I think macOS is superior now.
Exciting! Looks like I'm going to best buy later. Out of curiosity, when you say that you think macOS is superior, is that due to any specific hardware or performance issue, or is it just a matter of taste? Also, do you happen to remember whether or not brightness adjustment worked?

---

### Post by entangled on 2016-08-16
macOS becomes more attractive with use and I've even come to like Finder!

Specifically, macOS manages sleep and resume correctly all the time which I find very useful. Linux sleeps but won't resume on my machine. 
I think that is due to the graphic card issue where I suppose that connections are crossed, in hardware or firmware, so that main display looks like external and vice versa. I don't think graduated brightness control worked on linux, it was set to kick in but didn't. The display was either on or off (it did turn off, to cut energy use, at the set interval).

Other things: 
printing to my Xerox Phaser 6010 is easy to set up on macOS; possible but awkward on linux
scanning by Canon Lide 90, will not work at all on linux, but fine on macOS.
I've grown used to the macOS desktop and, to me, it is pleasing and functional.
I can install programming languages and editors as I like on macOS (and linux of course)
Arch linux, however, has a very good package manager, pacman, and libreoffice looks better on linux than on macOS.

---

### Post by nickles1995 on 2016-08-16
> **entangled said:**
> macOS becomes more attractive with use and I've even come to like Finder!

Specifically, macOS manages sleep and resume correctly all the time which I find very useful. Linux sleeps but won't resume on my machine. 
I think that is due to the graphic card issue where I suppose that connections are crossed, in hardware or firmware, so that main display looks like external and vice versa. I don't think graduated brightness control worked on linux, it was set to kick in but didn't. The display was either on or off (it did turn off, to cut energy use, at the set interval).

Other things: 
printing to my Xerox Phaser 6010 is easy to set up on macOS; possible but awkward on linux
scanning by Canon Lide 90, will not work at all on linux, but fine on macOS.
I've grown used to the macOS desktop and, to me, it is pleasing and functional.
I can install programming languages and editors as I like on macOS (and linux of course)
Arch linux, however, has a very good package manager, pacman, and libreoffice looks better on linux than on macOS.
Thank you for the reply. My mini displayport adapter is arriving on Thursday, so I will certainly be trying this anyway, but from your reply it sounds like this solution simply does the same thing as radeon.modeset=0 did above? Was the graphics performance abysmal compared to macOS? in particular, brightness adjustment is very important to me, so it is somewhat disheartening to hear that it didn't work for you. In any case, thanks for the suggestion and I'll confirm your results when I try it in two days.

---

### Post by nickles1995 on 2016-08-20
> **entangled said:**
> If it is any help I have a mid-2010 iMac with radeon 4670 GPU. 
The only way I have found to make linux booters show on the main screen is to plug a 'dongle' into the mini displayport.
The dongle is a mini-displayport to VGA adapter with three small resistors plugged into the VGA end.
Looking at the VGA end of the adapter face on, with the wider part at the top, there are three rows of holes.
The resistors are plugged into the first three holes on the right of the top row and also into the first three holes of the middle row, no crossovers.
Use about 75 ohm resistors, but probably OK between 50 and 100.
This seems to force the main display to carry the video output.

Linux boots well and runs OK at the correct resolution but I think macOS is superior now.
Ok, I've made the adapter and plugged it in now, and the machines behavior appears unaffected, still black screen after grub. Just to make sure, I made the dongle correctly, yes? 
[ATTACH=CONFIG]270770[/ATTACH]

---

