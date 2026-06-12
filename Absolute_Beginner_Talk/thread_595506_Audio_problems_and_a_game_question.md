---
title: "Audio problems and a game question"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by wiseguyxp on 2007-10-28
2 things here:

First, I just got Ubuntu installed and configured to my liking.  I mounted another hard drive I have and started playing music off of it, but first I had to download the mp3 codec for it.  It worked fine, but after a round of updates, I restarted the computer and it doesn't play songs anymore (no audio).  I tried multiple players, but it still doesn't work.  It doesn't give me an error message or anything.  Could it be that I have to install drivers for my sound card, even though it was working before?

Second, I'm a gamer, and I don't want to switch back to Windows if at all possible.  I tried loading World of Warcraft (I don't play anymore, but it was the first thing I could find) using Wine today and it was getting some really sad framerates.  Is this normal?  If I'm going to be playing games, will I need to dual boot to Windows?  I just looked and pretty much anything with any graphics at all has a pretty low fps.  I have a 512mb ATI Radeon x1650 Pro, so I shouldn't be getting low fps with a screensaver :S

Ubuntu Desktop 7.10 btw

---

### Post by Doc on 2007-10-28
Lots of problems are possible with regard to sound. Check out this post for some ideas on troubleshooting:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

The fact that your sound was working before suggests a minor configuration issue...are you sure your mixer settings are correct? What kind of hardware do you have? Try opening a terminal and posting the output of the command 'lspci', that may help. 

As far as WOW goes, if you're having issues with wine I'd check out cedega:

[http://www.cedega.com/]("http://www.cedega.com/") 

it seems to have great WOW support per the documentation.

Good luck

---

### Post by Doc on 2007-10-28
And FYI I play games a lot on Ubuntu, and my framerates are great for my purposes, but you may need to install the proprietary drivers for your hardware (if nvidia or ati), the default 'open' xorg drivers are ok for everyday desktop use but hardly optimal performance in opengl games. If your hardware is not one of those two manufacturers try searching the forum for tweaks specific for your hardware.

---

### Post by wiseguyxp on 2007-10-28
I followed the guide posted and found that my sound card is recognized and my volume wasn't muted... and that's about it :)

I typed the command and it said that the command wasn't found.

I'll keep cedega in mind if I keep having issues, but I kinda think it's a video driver problem.

I went to the ATI site and downloaded and installed their driver for my video card.  Everything seems okay except I can't access the Catalyst Control Center, which gives me some error about the driver not being installed.  I'm checking the configuration utility right now and if you don't hear back from me, I probably nuked my video drivers on accident :)

---

### Post by wiseguyxp on 2007-10-29
Ok, I did something with the video card driver and now the Catalyst thing works and my sound magically started working.  Even though Catalyst is working and detects my card, it says my bus speed is 0x (it's an 8x card).  Screensavers and any video is still running at really low fps.  I'll check back tomorrow.  I'm done with this for tonight :)

---

### Post by Crafty Kisses on 2007-10-29
> **wiseguyxp said:**
> 2 things here:

First, I just got Ubuntu installed and configured to my liking.  I mounted another hard drive I have and started playing music off of it, but first I had to download the mp3 codec for it.  It worked fine, but after a round of updates, I restarted the computer and it doesn't play songs anymore (no audio).  I tried multiple players, but it still doesn't work.  It doesn't give me an error message or anything.  Could it be that I have to install drivers for my sound card, even though it was working before?

Second, I'm a gamer, and I don't want to switch back to Windows if at all possible.  I tried loading World of Warcraft (I don't play anymore, but it was the first thing I could find) using Wine today and it was getting some really sad framerates.  Is this normal?  If I'm going to be playing games, will I need to dual boot to Windows?  I just looked and pretty much anything with any graphics at all has a pretty low fps.  I have a 512mb ATI Radeon x1650 Pro, so I shouldn't be getting low fps with a screensaver :S

Ubuntu Desktop 7.10 btw

Post the following output:
```
lspci
```

---

### Post by wiseguyxp on 2007-10-29
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c1 (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Unknown device 71e1 (rev 9e)

also my xorg.conf wants me to make a "real" xorg.conf as it says

---

