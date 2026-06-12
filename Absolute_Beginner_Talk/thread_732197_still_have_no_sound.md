---
title: "still have no sound"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by awashington on 2008-03-22
I was told to download alsa and recompile but i'm not sure how to do this



*-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: fast devsel, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

---

### Post by kyphi on 2008-03-22
If you have a desktop computer, the best solution is to disable the onboard sound chip in the BIOS and install a sound card.

The Creative Soundblaster Live is cheap and works very well in Ubuntu.

---

### Post by erginemr on 2008-03-22
You may want to have a look at this first:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by awashington on 2008-03-22
yeah just tried that this is all i got.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

---

### Post by erginemr on 2008-03-22
Sorry, I forgot to tell you that you need to enable the backports repository from Synaptic -> Software Sources first.

---

### Post by awashington on 2008-03-22
yeah thats enabled and still having the same msg.....i'm gonna take a hammer to this damn thing........:{

---

### Post by oedha on 2008-03-22
have you insert a line in your /etc/modprobe.d/alsa-base ?
you should insert something like :=>  options snd-hda-intel model=MODEL

you can found the detail on :=> [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by erginemr on 2008-03-23
Don't worry. Assuming that your Linux kernel has same 2.6.22-14 version, which you can learn learn from the terminal with:
```
uname -r
```
you may download and install the same package from the following link:
[http://packages.ubuntu.com/gutsy/linux-backports-modules-2.6.22-14-generic](http://packages.ubuntu.com/gutsy/linux-backports-modules-2.6.22-14-generic)

And in addition to oedha's post, who has proposed an alternative candidate for solution, you may also pay a visit to the following topic where quite a few model names have been listed fror HDA intel cards:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by awashington on 2008-03-23
no haven't tried that. can i do that in the terminal

---

### Post by erginemr on 2008-03-24
Yes. You can go to Main Menu -> Apps - > Terminal and input the commands there. And for the Debian package, you can download it and install by double clicking on it. If you have the backports repository (see the attached screenshots), you can also download the same from Synaptic. (But as a disclaimer; these are still shots in the dark, may or may not work in your system)

Alternatively (or if the above does not work, please refer to this topic:
[http://ubuntuforums.org/showthread.php?t=714635](http://ubuntuforums.org/showthread.php?t=714635)

and particularly this thread by Temujin:
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

to compile and update your ALSA drivers to the latest version (which was your primary goal in your first post) in an effort to have it recognize your sound chip.

---

