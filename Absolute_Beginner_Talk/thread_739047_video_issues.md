---
title: "video issues"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-29
i have got two issues:
1.none of the players,like amarok,totem,VLC plays videos as sharp as it is done on my windows xp.the desktop effects too are not running,i.e.compiz is failing me.
2.i can't play videos on the internet,for example youtube videos,though i have installed flash player,and the video even appears,but never plays when i try to.

---

### Post by gobbles414 on 2008-03-29
> **stonecoldjha said:**
> i have got two issues:
1.none of the players,like amarok,totem,VLC plays videos as sharp as it is done on my windows xp.the desktop effects too are not running,i.e.compiz is failing me.
2.i can't play videos on the internet,for example youtube videos,though i have installed flash player,and the video even appears,but never plays when i try to.

Please answer these questions. Your answers will help us to help you:

* What version of Ubuntu are you using?
* What happens in *System => Administration => Restricted Drivers Manager* in Ubuntu?
* What graphics resolution are you using in XP?
* What resolution are you using in Ubuntu?
* What is your graphics card?
* What kind of monitor are you using?
* For part one, what video formats are you playing? Examples: WMV, MOV, MPEG...
* How did you install Flash Player (some methods have bugs)?

We can help you much better once you have answered the above questions. :KS

---

### Post by stonecoldjha on 2008-03-30
1.i am using ubuntu 7.10.
2.in system>administration>restricted driver managers,it shows no restricted drivers required.
3.in xp i use a resolution of 1024*768.
4.the same resolution in ubuntu.
5.my graphics card is intel graphics controller of the chipset family.
6.i am using a 15" acer AC515 crt monitor.
7.the problem is with all the formats.
8.i tried to install flash player from the terminal..........as instructed in one of my earlier posts.

---

### Post by prismpirate on 2008-03-30
If you really want compiz to work, then you can always try the command:

```

SKIP_CHECKS=yes compiz

```

It will be buggy, as your graphics bard is probably blacklisted


Regarding your flash player, you should have installed it by visiting a website which requires flash, and clicking on "Install Missing Plugins", which will show a window similar to that in Windows XP.

---

### Post by taavikko on 2008-03-30
It's not necessary to install flash that way.
```
sudo apt-get install flashplugin-nonfree
```
and if it's not working correctly
```
sudo dpkg-reconfigure flashplugin-nonfree
```
should clear that issue.

Maybe installing ubuntu-restricted-extras could solve the video-issues
because ubuntu is using by default totem-gstreamer for video playback, and not all gstreamer things are installed by default.

---

### Post by gobbles414 on 2008-03-30
Hi stonecoldjha,

**SHARPNESS:** Ah... You're using a CRT! I've discovered that "refresh rates" can really change the appearance of sharpness on CRT monitors. My guess is that your refresh rate in Ubuntu is lower than in XP. In my experience, lower refresh rates do not look as sharp as higher rates. Go *System => Administration => Screens and Graphics* and try to select a higher refresh rate.** While your in that control panel, please discover what graphics driver you are currently using. Post you results.** Another possibility is that 1024x768 is not your monitor's "native resolution". Native resolution is usually sharper than other resolutions, and is usually equal to the maximum resolution of a monitor. Consult the documentation that came with your monitor for more info. It's less likely that installing *ubuntu-restricted-extras* will be of any help. But maybe try it anyway...

**FLASH:** You may have made a mistake in your manual installation of your Flash player. Did you install the Flash player to *usr/lib/firefox*? The *usr/lib/mozilla* location suggested by the installer does not work in Ubuntu -- at least for me. As you probably know, there's a well-documented bug in Ubuntu's Flash player installer. I'm not sure if the Flash player installation bug has been fixed for Ubuntu 8.04 or not. But at least in Ubuntu 7.10, manual installation is the best method. In fact: apt-get, Synaptic, Add/Remove, and the automated Firefox installation have all failed for me. This includes *flashplugin-nonfree*, which can be installed on its own or as part of *ubuntu-restricted-extras*.

Does any of this help?

---

