---
title: "Re-sizing windows for low resolution screens."
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Kappity on 2007-10-26
It appears that the maximum screen resolution available on this old laptop is 800x600.  That seems to be confirmed by the information about this model on Thinkwiki.  I found a lot of information on this forum about editing xorg.conf, so I had a shot at that anyway, but it seems that 800x600 is it.  There are threads about how to deal with this kind of thing, but they all assume that you'll be able to get a higher resolution.

Assuming 800x600 is all that this computer will do, is there any way to re-size windows so that the entire window fits on the screen at this resolution?  For most applications that I've used, this is not an issue.  There are a few, however, that are either unusable, or not fully usable, because part of the application is off screen.  Examples:

Iagno (a gnome reversi game)

Evolution.  I've just been using Thunderbird for Email, and it all fits on the screen.  However, I've discovered that if I sync my PDA with Ubuntu, the Calendar, memo, and address information is synced with Evolution.  Most of it fits on the screen, and I can use the functions, but there is enough missing on the bottom and on the right to make some functions unusable.  Also, during setup, some of the buttons were off the bottom of the screen.  I had to tab to them, guess which one I was on, and hit enter.

Various setup screens.  For example, I was just setting up audio alerts, and there was stuff off the bottom of the screen.

I may just have live with this until I get Ubuntu on a better computer.  However, if there are workarounds, hacks, parts of the help files that I've been missing ;), I'd appreciate knowing about them.

Incidentally, I tried hooking up the laptop to my 17 inch LCD monitor, but I can still only get 800x600.  I assume it must be due to the video card.  I wouldn't be using it with an external monitor most of the time anyway.

---

### Post by linuxlizard on 2007-10-26
This is actually something that has annoyed me with kubuntu on my folks computer. My elderly mother doesn't see so well any more, so 800x600 is necessary for her. But a lot of the control screens don't have scroll bars on them, (and some apps like the 1st gimp window for example are the same) and the bottom of the window reaches down to the nether regions below the screen where it can't be seen or clicked on.

I've never found a solution- fortunately my mother mostly just uses firefox and open office writer, so after I get the computer set up after an install, I don't have to mess with the resolution any more.

---

### Post by Frak on 2007-10-26
Try going to Applications -> Accessories -> Terminal and paste the following
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Kappity on 2007-10-26
> **Frak said:**
> Try going to Applications -> Accessories -> Terminal and paste the following
```
sudo dpkg-reconfigure xserver-xorg
```

Thanks, I gave it a shot, but it seems to be just another way of editing xorg.conf, which I'd already tried without success (using Emacs).  There are a bout a zillion threads on how to do this.  No better luck this time.

It would be great if it turned out that this computer really were capable of higher resolutions, but that may just turn out not to be the case.  I'm still interested in my orginal question.  Assuming that 800x600 really is all this computer this will do, is there anything I can do to resize windows to fit the screen, if the application itself won't allow that?

---

### Post by Frak on 2007-10-26
What video card do you have?

---

### Post by Kappity on 2007-10-26
> **Frak said:**
> What video card do you have?

ATI Technologies Inc Rage Mobility P/M AGP 2x.  At least, that's what Ubuntu auto-detects.

[Here is]("http://thinkwiki.org/wiki/Category:A20m") the Thinkwiki page for the computer; it's the one with the 12.1 inch screen.  Looking at those specs, it seems like it's the screen rather than the video card that imposes the 800x600 limitation.  Perhaps if I plugged in the external monitor and then configured it . . . but that's pointless.  This is being used as a laptop.

---

### Post by tibellus on 2007-11-07
I have the same problem with an old PII at 400 MHz. Many windows (almost all) don't fit on the screen, because Ubuntu chooses 800x600 as default resolution, although my monitor can perform better.:) On Vector Linux, I could get it working at more than 1280x1024. I know my video card is lame - an NVidia with only 32 MB of RAM -, but why do other operating systems work and Ubuntu doesn't?:guitar:

---

### Post by maharbA on 2007-11-07
I have an old computer plugged into a TV. Its resolution is set to 800x600 as a compromise (if you think that poses problems, try 640x480) since it's the highest rez I can see on a TV screen.

I've been looking for a way to fix this for years without success, so I'll definitely be subscribing to this thread :)

I have found one workaround, though. If you hold Alt you can click anywhere in the window to move it around. So you can hang the top off the screen to see the bottom. It's a pain, but it's all I've got.

---

### Post by Kappity on 2007-11-08
> **maharbA said:**
> (snip) . . .
I have found one workaround, though. If you hold Alt you can click anywhere in the window to move it around. So you can hang the top off the screen to see the bottom. It's a pain, but it's all I've got.

Thanks, I didn't know about that one.  Definitely better than nothing.

My eventual solution will be to put Ubuntu on a better computer, but for now . . .

---

### Post by tibellus on 2007-11-10
Hello again:)

Last night I was trying to upgrade from 7.04 to 7.10, and a power failure made my system inoperable, so I had to reinstall Ubuntu this morning. At this moment, I am going once more through the update and upgrade process. Anyway, this is not the thing I wanted to say, but with the problems created by the power failure, I've learned what driver uses Knoppix for my Voodoo graphics card. After you run ```
sudo dpkg-reconfigure xserver-xorg
``` try to choose tdfx as the driver for your video card. I tried the other ones, like voodoo, or nv, or nvidia... none of them worked, so after I've tried this option, I can use the maximum resolution of my monitor without any problems.

When I used the vesa driver and changed to a lower resolution than the default one -from 1280x1024 to 1024x768- the monitor only outputed colored lines:) Tdfx is the best solution for me right now, I'll stick with it unless I find something better.

---

### Post by maharbA on 2007-11-10
I just checked in Gutsy and (under the SYSTEM>PREFS>WINDOWS) you can easily change the Alt+click and drag shortcut to either Conrtol or Super/Win keys. That was thoughtful of the devs

---

### Post by lupin492 on 2008-01-24
> **tibellus said:**
> Hello again:)

... After you run ```
sudo dpkg-reconfigure xserver-xorg
``` try to choose tdfx as the driver for your video card. I tried the other ones, like voodoo, or nv, or nvidia... none of them worked, so after I've tried this option, I can use the maximum resolution of my monitor without any problems.

When I used the vesa driver and changed to a lower resolution than the default one -from 1280x1024 to 1024x768- the monitor only outputed colored lines:) Tdfx is the best solution for me right now, I'll stick with it unless I find something better.


I'll post this info here cause 3DFx is mentioned, and I came here looking for info on Voodoo 3 3000.
As I've found till now, 'voodoo' is the appropriate driver for Voodoo cards up to series '2'.  For Voodoo 3 series, 'tdfx' is the driver to look for.
Furthermore, if you want to use acceleration (OpenGL), you will need one more library: 'libglide3' (in my case).   By the way, you will only be able to get acceleration selecting resolutions up to 1024x768, AND 16-bits color depth.  Any bigger will turn it off.  You can check it is working typing 'glxinfo | grep direct' in a console terminal; if it answers 'YES', it is working.
On the other hand, if you don't need acceleration, you can set it for example to 1440x900-24bit, which is the setting I mostly use.
The last one: if you even want to turn-on your TV-out, it is said you only need to install and configure 'lm-sensors' package and write 800x600PAL and 640x480PAL in your resolutions line in xorg.conf, but I was not able to make it work till now .
Hope this is useful for somebody. Regards!  :popcorn:

---

### Post by lupin492 on 2008-01-26
Addition: I recently discovered IT IS possible to have acceleration at resolutions beyond 1024*768 / 16bpp using Voodoo video cards.  To read the  procedure go to:
**[http://ubuntuforums.org/showthread.php?p=4213920](http://ubuntuforums.org/showthread.php?p=4213920)**  and look for the original **cbrinegar**'s tutorial, and, if you need a little more help, look for my own explanations (lupin492).
Good luck!

---

