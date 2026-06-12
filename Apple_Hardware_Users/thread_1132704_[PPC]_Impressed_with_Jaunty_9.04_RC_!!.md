---
title: "[PPC] Impressed with Jaunty 9.04 RC !!"
date: 2009-04-22
forum: Apple Hardware Users
---

### Post by stream303 on 2009-04-22
This is looking to be the best release for ppc yet.  Nothing like posting observations about the rc a day or two before release, (busy with other obligations) but here goes...

System - G5 iMac / 1.5gb / 1.8ghz / 20" nvidia graphics

**1)** Using the desktop-live cd, the fans were totally quiet!  YES - this used to be a problem for G5's during installation where the fans would absolutely roar until after the first reboot.  Fixed.

**2)** No CPU-frequency-scaling enabled by default.  I personally like frequency scaling since it does save me 10 watts of power as measured at the ac outlet.  Noted that powernowd was too sluggish for my needs, and installed my favorite alternate for single-cpu ppc boxes:  CPUDYN.  (audio/video editors take note if you need frequency scaling with low-latency)

**3)** Pacman-like splash screen! :)  I wouldn't feel at home if I didn't see this.  Unfortunately, splash screens on ppc tend to either just look funky, or put some graphics cards into a locked state.  Solution:

  A. add "nosplash" (without quotes) as an additional kernel parameter when you reach the second-stage yaboot boot: prompt, ie
```
install-live-powerpc64 nosplash
```

  B. To make this option permanent, edit your /etc/yaboot.conf file, and change the APPEND= line to nosplash instead of splash.  Follow up with *sudo ybin -v*

(in this note I didn't want to go too deeply into other apple quirks like trying *video=ofonly* as well.  My ppc box didn't need it.

**WPA WIRELESS**
Although I still couldn't get my airport-extreme card to work with wpa, I'm happy to report that two USB wireless sticks work out of the box without having to hunt down firmware etc.  So, both my Belkin F5D7010 and Netgear WG111v2 work perfectly with wpa.  Network Manager 7 seems to have no problems with both the airport and a usb wireless stick attached - I just configure and connect using the usb wireless.  Believe me, I actually like configuring /etc/network/interfaces by hand with wpa_supplicant and wext.conf et al rather than using Network Manager, but hey, this time it seems to be working.

(This actually works out nicely since I use the usb wireless sticks with Jaunty, and the airport-extreme with OSX to get wpa)

Since my box is using nvidia (well, the nv driver actually) xorg configuration was automatic and didn't have to edit anything.  ATI users may have a different experience.

It was a joy not to experience Intrepid's inability to find the cdrom drive, and other up-front problems.  Remember I'm using Ubuntu, so I can't speak for Kubuntu / Xubuntu.

All in all, I think 9.04 is shaping up to be the best release for ppc yet.  Maybe we can convince them to stop the splash screen for 9.10. :)  For the least pain, I'd recommend a late-model G4 or G5 that has at least 256mb or more of ram.  G3 users will definitely want to go light or perhaps do a low-memory / server + wm only install.

And on my 20" imac, like all other ppc distros that use the nv driver, my screen is shifted to the right about a quarter-inch.  I'll have to recompile the xorg nv driver to take care of that as discussed elsewhere.

But man, for an "unofficially supported" port, 9.04 rc is doing very well indeed.

---

### Post by tiresia on 2009-04-22
> **stream303 said:**
> This is looking to be the best release for ppc yet.  
I think you are right! Also because I install it formatting my HD with ext4, and I noticed a quite big difference - it boots faster (and check faster the system)

And last but not least, we have now a Xubuntu LiveCD!!! A great job!

---

### Post by stream303 on 2009-04-22
Yep - I forgot to mention that I still don't have any real backlight control, so I'm using some of the darker themes.

Xubuntu users might notice the brightness controls that although they didn't seem to control the screen brightness in hardware, they seems to have some magic (custom gamma values?) that can help.

Pretty jazzed right now - although I think most should just wait a day or two for the actual release.  Nice hearing from you!

---

