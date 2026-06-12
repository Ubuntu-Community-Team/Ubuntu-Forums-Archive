---
title: "Widescreen monitor and wrong partition size"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-06-27
Hey everyone I'm pretty new to linux in general. I've tried out a few live CD's in the past but really I've never installed a distro because none I've found ever really worked that good.

Tried the Ubuntu CD today and was amazed how well it worked. my audio card and internet just worked, so I decided to hit install. I was further amazed at how it let me pick and partition the hard drive to put it on.

But I have a couple of problems.

1. I misunderstood the partition instructions. So I ended up with opposite size I wanted for Ubuntu. Is there anyway to fix this without reinstalling everything?

2. I have a new wdescreen LCD monitor. The native resolution is 1440x900. Ubuntu won't let me select this resolution. In fact it won't let me select any other resolution then 1280x1024 and any other refresh rate besides -32332 Hz. So everything is stretched looking.

My video card is an older ATI radeon 7000 series. I don't know if that's any help.

Aside from these two problems I'm surprisingly very pleased with this linux os.

---

### Post by MetalMusicAddict on 2006-06-27
[QUOTE=roxics]

But I have a couple of problems.

1. I misunderstood the partition instructions. So I ended up with opposite size I wanted for Ubuntu. Is there anyway to fix this without reinstalling everything?[/QUOTE]
Unless you used LVM (Logical Volume Management) I dont think so.
[QUOTE=roxics]2. I have a new wdescreen LCD monitor. The native resolution is 1440x900. Ubuntu won't let me select this resolution. In fact it won't let me select any other resolution then 1280x1024 and any other refresh rate besides -32332 Hz. So everything is stretched looking.

My video card is an older ATI radeon 7000 series. I don't know if that's any help.

Aside from these two problems I'm surprisingly very pleased with this linux os.[/QUOTE]
Install the ATI drivers, reboot, then do a **sudo dpkg-reconfigure xserver-xorg** in a terminal to pick all the resolutions and refreshes you need.

---

### Post by roxics on 2006-06-27
I couldn't find the ATI drivers. But I did find Automatix and easyubuntu and installed both of those. Now I've got my screen resolution working right and alot of apps installed. Pretty cool. 
But yeah my partition is still an issue.

Also I've found another issue, I'll search for a solution in a minute but while I'm typing this reply I'll include it incase it's an easy fix.
I use a USB keyboard and so from my boot screen I can't select the OS to run.

---

### Post by siccness on 2006-06-27
[QUOTE=roxics]
I use a USB keyboard and so from my boot screen I can't select the OS to run.[/QUOTE]

Is there a BIOS option with the following:
Enable/disable legacy USB support, if so, Enable it. (You might have to actually have a PS/2 Keyboard to enable it, not sure).

---

### Post by MetalMusicAddict on 2006-06-27
[QUOTE=roxics]I couldn't find the ATI drivers. But I did find Automatix and easyubuntu and installed both of those. **Now I've got my screen resolution working right and alot of apps installed. Pretty cool.** 
But yeah my partition is still an issue.

Also I've found another issue, I'll search for a solution in a minute but while I'm typing this reply I'll include it incase it's an easy fix.
I use a USB keyboard and so from my boot screen I can't select the OS to run.[/QUOTE]
Glad to hear you got it working. ;) Have fun and learn.

---

### Post by roxics on 2006-06-28
[QUOTE=siccness]Is there a BIOS option with the following:
Enable/disable legacy USB support, if so, Enable it. (You might have to actually have a PS/2 Keyboard to enable it, not sure).[/QUOTE]

Thanks, that did it.

---

