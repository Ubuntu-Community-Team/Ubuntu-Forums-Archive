---
title: "MacBook keyboard not recognized on boot"
date: 2008-09-29
forum: Apple Hardware Users
---

### Post by undefined117 on 2008-09-29
I have a black MacBook 2,1. I've installed K/Ubuntu a few times. My partitions for each:

UBUNTU 8.04 -- gone due to hard drive crash -- disk wiped and partitioned using gparted, did not use rEFIt
sda1 -- ext3 for /
sda2 -- ext3 for /home
sda3 -- swap

KUBUNTU 8.04 KDE 4.1 -- current -- GPT created with Mac OS's Disk Utility, then edited with gparted; rEFIt used to sync MBR/GPT, but not for boot
sda1 -- EFI
sda2 -- hfsplus currently empty
sda3 -- ext3 for / -- blessed
sda4 -- ext3 for /home
sda5 -- swap

The Ubuntu installation suffered from frequent slow boots (30 to 40 seconds).

I've read the bug [here](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/60177) about the grub + keyboard problem as well as how to bless the boot partition in [this topic](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21).

I have blessed this Kubuntu boot partition. However, it still suffers from a slow boot. This happens both by booting through rEFIt and through the Mac's built-in partition chooser (pressing alt at startup).

I'm confused because I thought the bless was supposed to solve the slow boot problem..

The slow boots always coincide with the keyboard not being recognized. I've tried ssh'ing into my machine after kdm loads then running *sudo modprobe usbhid*, to no avail. My current "solution" to this: after grub loads, when the "Loading... please wait" message flashes, press and hold down the power button. This will force shutdown the machine, but you must reboot it almost immediately after it shuts down for the keyboard to be recognized. The boot process is also much faster (8 seconds). This worked in both installations.

I've taken notes of my Kubuntu installation [on my blog](http://www.artofproblemsolving.com/Forum/weblog_entry.php?p=1267213), if it helps.

Does anyone know of a solution to the slow boot/keyboard problem that doesn't involve force-rebooting? It can't be good for my laptop.. :(

---

### Post by cyberdork33 on 2008-09-30
I'd make sure you have all the updates for your Mac as the keyboard problem in grub (and other bootloaders) on most Macs was fixed awhile ago.

Also, if you are not installing OS X or anything, why don't you just make the drive normal MBR format? Why are you using GPT?

---

### Post by undefined117 on 2008-09-30
Yes I have an external drive with Mac OS 10.5.5 installed. In fact, I ran software update yesterday just to be sure. No luck.

I would normally have formatted it with MBR as I'm very happy with a single-boot Linux system. I just wanted to see if formatting it with GPT made any difference -- it appears not to have made any difference. :|

I'm not even sure if this is a grub problem; if I let it boot with the keyboard unrecognized then reboot using my usb mouse, pressing alt at the gray screen doesn't work. If I connect my external drive and let rEFIt load, I can't choose anything as the arrow keys don't work (nor anything else). Then it just boots to Mac OS X with the keyboard still dead.

---

### Post by cyberdork33 on 2008-09-30
what other USB devices are connected? have you tried other USB ports?

---

### Post by undefined117 on 2008-09-30
Other USB devices? er my external drive, and through a USB hub: mouse and printer.

It never occurred to me, though, to rip out the built-in keyboard.. :biggrin:

---

### Post by cyberdork33 on 2008-09-30
> **undefined117 said:**
> Other USB devices? er my external drive, and through a USB hub: mouse and printer.

It never occurred to me, though, to rip out the built-in keyboard.. :biggrin:
try removing uneeded devices and see if you get the same behavior.

---

### Post by undefined117 on 2008-09-30
Oh wow -- I unplugged the USB hub and it seems to boot in 3 seconds!

Well now that I think about it, my mp3 player did the same thing. It would be unrecognized until I unplugged/plugged it back in.

What a simple fix. XD But why is this so? How'd you think of that?

---

### Post by cyberdork33 on 2008-09-30
> **undefined117 said:**
> What a simple fix. XD But why is this so? How'd you think of that?
Cause it happens to me all the time when I leave my iPod connected. It is like the Mac is searching for a bootable volume on it or something...

---

### Post by undefined117 on 2008-09-30
I see. Anyway thanks!

---

