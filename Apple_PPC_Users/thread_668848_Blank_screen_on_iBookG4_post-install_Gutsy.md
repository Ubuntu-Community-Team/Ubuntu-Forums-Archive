---
title: "Blank screen on iBookG4 post-install Gutsy"
date: 2008-01-15
forum: Apple PPC Users
---

### Post by FritsHorzol on 2008-01-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Installed gutsy on my iBook G4 12"

Had to use the live-nosplash-powerpc to get the cd to boot (had a blank screenthere as well)
Now after reboot i got the blankscreen again. The faq is telling me to put ide-core in the initramfs/modules file and generate some stuff, which is a silly thing to say because i have no way of getting into my system let alone running commands and editing files. 

But i worked around that by booting the livecd again and chrooting into my freshly installed system. So i edited the file i ran the updatething and go back to booting from disk, still i get the blank screen

i think that this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337") is what i have but the workaround in the faq is the same so i might be wrong

Anyone?

---

### Post by stream303 on 2008-01-17
I just got Gutsy installed on my G4 iBook (late 2004 model), but I used the alternate text-based boot CD.  I ran into a few snags of my own with the alternate - but thanks to the gang here Gutsy is usable even if all the bugs aren't totally worked out.

1. Wiped OSX and installation took what seemed like *forever*, although it eventually finished.  Something was hogging the cpu causing the iBook internal fans to spin hot.

2. Upon reboot, I got hit with the date/time bug.  Had to ctrl-alt-f1 and change the date in the blind since I couldn't see anything.  Used the PPC bug/faqs to help out here.

3. Now I can get past login - however the Network Manager was the culprit for hogging 100% of the cpu.  Removed Network Manager and had to bring up the ethernet interface with the old standby:

sudo ifup eth1

in gnome terminal.

(This is really strange - even though I got rid of Network Manager with synaptic, I can still bring up the gnome network manager!  At least it isn't doing the runaway process anymore - weird!)

4. CPU frequency scaling was stuck at 1.2 ghz.  At least the cpu isn't running any runaway process with network manager gone.  (used TOP or my favorite, HTOP to find this hogging process).  Disabled POWERNOWD service.

5.  Re-enabled POWERNOWD service, and cpu scaling is working as verified by the scaling applet and cooler system at 667 mhz most of the time.  I always add the frequency scaling applet to the top panel to keep an eye on things...

6.  Performed the X11 tweaks for my ATI card, and did some other tweaks like IDE-CORE as shown in the PPC faqs.

7. Stmiller got me going with audio by adding snd-powermac and snd-seq to /etc/modules.  Whew.  Thanks again!

8. I found that I had to manually configure the Ubuntu repositories to be "trusted", and updated all the software without any problems.

9. Like my Ubuntu PC, Rhythmbox seems problematic, so I stick to Totem Movie Player, or VLC for playing my tunes, which are typically just the ogg-vorbis streams from [www.hbr1.com](www.hbr1.com)  (also the default radio stations in Rhythmbox)

10. Although not a bug, I just disable the video affects for snappier performance on the iBook.

11.  I don't like messing around with my /etc/resolv.conf file for DHCP, so on my home network router, I configure the primary and backup DNS servers in the *router's* setup page for OpenDNS 208.67.222.222 and 208.67.220.220.  Done!

I haven't tried wireless.

Hope some of this helps.  I haven't tried using Gutsy on my G5 iMac yet.....

---

### Post by FritsHorzol on 2008-01-17
Well i got the ide-core modul loaded now with the Linux break=top routine
but still after i exit i get the blank screen with just a cursor and then completly blank
the frustating thing is that i cant get any logs or any feedback whatsoever

the problem isnt the ide_core anymore, maybe it never was because its loaded now.
anyone else having blank screens even after loading the ide_core module?

---

