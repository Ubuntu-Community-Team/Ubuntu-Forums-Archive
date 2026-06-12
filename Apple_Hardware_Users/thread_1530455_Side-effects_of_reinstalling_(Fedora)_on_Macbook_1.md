---
title: "Side-effects of reinstalling (Fedora) on Macbook 1,1"
date: 2010-07-13
forum: Apple Hardware Users
---

### Post by renkinjutsu on 2010-07-13
I broke my previous installation because i switched between kernels running btrfs (dumb), so i reinstalled
Fedora is my preferred distribution, but anybody (if interested) can benefit from this


Side effects:
I finally got around to trying those powersaving techniques
> I usually lower the brightness of my LCD to the lowest setting
I bring down unused interfaces like eth0
Disable Bluetooth when its not in use
I've switched to a minimalist - "X, feh for background, iwconfig+ifconfig for wifi, xfce4 panel, xfsettingsd, PekWM" desktop that uses only 88MB of RAM while booted to graphics (also had to recompile kernel to get rid of gunk)
The macbook 1,1 only has 512MB of RAM, so keeping ram usage low helps to keep it from swapping and spinning the harddrive.
Appended usbcore.autosuspend=1 to my kernel line (support compiled into kernel)
Also, compiled "aggressive power saving" into my snd_hda_audio driver
and really, the rest, i just installed powertop and followed all the tips that showed at the bottom (like echo'ing "min_power" to the link_power_management_policy for the SATA link located somewhere in /sys/class/scsi_host/*

NOTE: Now i get 4 hours of battery life out of my macbook 1,1 with moderate usage. Over 4 hours if I leave it alone (consumes roughly 11 watts of power.
NOTE: Also, when left alone, my macbook is actually pretty cool/warm to the touch when before, it just heated up for no reason
Finally got Pulseaudio to work
> got pulseaudio to launch even before login using /etc/rc.local - that eliminated the dummy audio output problem


---

