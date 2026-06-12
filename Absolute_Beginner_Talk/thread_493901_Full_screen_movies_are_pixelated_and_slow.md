---
title: "Full screen movies are pixelated and slow"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by freak_lick on 2007-07-06
I use 7.04 Ubuntu and VLC player for movies.
I had some problems w/playing video files but i managed that - but now i have another problem:
When I do full screen on VLC my movies are pixelated and are really slow..
When it's not full screen it all ok...
Plz HELP

---

### Post by freak_lick on 2007-07-06
And i just don't get why i cant' play any movie files from server or even burn cd with files from server..??
Is this UBUNTU issue or ...??

---

### Post by HereInOz on 2007-07-06
Regarding the poor performance playing full screen videos, my first question would be:

What is your video card, and do you have it properly configured?

When you say they are slow, do you mean that the movie runs slow, or the screen updates are slow and jerky?  If the latter, this also points to a video card issue or lack of video card memory. 

Burning CDs is always best done with the file locally, rather than across a network, unless you have a fast network which you trust implicitly.  Is the "Server" a Windows machine, or is it another Linux box?  If Windows, you could be running into the problem that Linux is not able to write to a file on an NTFS share.

---

### Post by freak_lick on 2007-07-06
> **HereInOz said:**
> Regarding the poor performance playing full screen videos, my first question would be:

What is your video card, and do you have it properly configured?

When you say they are slow, do you mean that the movie runs slow, or the screen updates are slow and jerky?  If the latter, this also points to a video card issue or lack of video card memory. 

Burning CDs is always best done with the file locally, rather than across a network, unless you have a fast network which you trust implicitly.  Is the "Server" a Windows machine, or is it another Linux box?  If Windows, you could be running into the problem that Linux is not able to write to a file on an NTFS share.

Screen updates are slow and jerky :-)
I have integrated graphics and when i installed ubuntu i didn't configured it all..
Server is Linux machine with Microsoft share,and i can read/write on it's folders..
I have Gigabit Lan on my comp and also on Server so i trust it.
Any help??

---

### Post by freak_lick on 2007-07-06
No 1 knows the soultion for this problem or...???

---

### Post by Ssj3_man on 2007-07-06
integrated cards are your problem ;)

---

### Post by forrestcupp on 2007-07-06
> **Ssj3_man said:**
> integrated cards are your problem ;)

True for the most part, but it depends on what kind.  If it's a Geforce 6100, it's not great for opengl, but it should be able to handle full screen vids.

You need to figure out what kind of video chip you have, and decide whether it needs proprietary drivers to speed things up.

---

### Post by freak_lick on 2007-07-10
Ok i found what kind of integrated graphics i have :
It's Intel 82865G Integrated Graphics Controller
on ASUS P5P800 Motherboard
and on windows in full-screen movies i have normal videos...
Any solution how can i configure my graphics to work properly in Ubuntu??

---

### Post by freak_lick on 2007-07-10
I disabled Desktop effects and now it's normal speed but still video is pixellated....

---

### Post by freak_lick on 2007-07-11
PLease HELP!!!

---

### Post by SyberKowboy on 2007-07-11
Running an integrated Intel chipset too on a new laptop and having the same stupid problem. How do I  configure Feisty for Intel video chipset?

---

### Post by freak_lick on 2007-07-12
> **SyberKowboy said:**
> Running an integrated Intel chipset too on a new laptop and having the same stupid problem. How do I  configure Feisty for Intel video chipset?

Guess we both don't have luck with watching movies on Ubuntu...

---

### Post by SyberKowboy on 2007-07-12
unless we watch them all small and in a seperate window. I've tried everything i can think of including new drivers and various settings in my xorg.conf. It's really annoying!

---

### Post by MissDjax on 2008-03-03
I have the same issue and I have an ATI x800 pro. So this isn't a integrated gfx card issue.

---

### Post by dgrafix on 2008-03-03
Intel cards are awful for openGL acceleration. I would never buy any laptop with one of these. If its a desktop you have then buy a cheap geforce4 or something.... anything but intel! If its a laptop then you have my sympathies.

It sounds to me like you are not getting the 2D acceleration to work properly or some filtering is switched off. I can play videos in 1280x1024 fullscreen non pixelated from a fileserver without any problems. This is on a 800mhz duron. I do have an ati card though.

---

### Post by epinephrine on 2008-03-09
i also experience this issue with my ati hd 2600. also compiz is enabled.
how do you resolve the pixelated issue on VLC? (VLC video output is set to x11)

---

### Post by epinephrine on 2008-03-10
bump! still no solution? :) a little help here would be appreciated greatly!

---

### Post by prshah on 2008-03-10
> **freak_lick said:**
> I use 7.04 Ubuntu and VLC player for movies.
I had some problems w/playing video files but i managed that - but now i have another problem:
When I do full screen on VLC my movies are pixelated and are really slow..
When it's not full screen it all ok...
Plz HELP

Are you using 7.04 or 7.10... your profile says 7.10, you say 7.04.

Turning off compiz helps with most video issues on 7.10. Ditto Beryl on 7.04.

I run VLC and MPlayer on an Intel graphics chipset and everything is just fine.

Cheers,
PRShah

---

### Post by elustran on 2008-03-20
I'm having the same problem.  I tried turning off compiz (didn't looke like it was even running, actually) but that had no effect.  I'm having pixilation problems when any video is zoomed using any player.

I'm running Ubuntu 7.10, radeon 9800pro, fglrx drivers.  Was experiencing the problem on 7.04 too, and I hoped that there might be some better driver handling in 7.10 that would fix the flaw.

I'm tired of this problem, and I'm certainly not the only one experiencing it.

---

