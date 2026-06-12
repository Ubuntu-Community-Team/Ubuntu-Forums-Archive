---
title: "can't boot on mac pro"
date: 2009-12-12
forum: Apple Hardware Users
---

### Post by davidRUK on 2009-12-12
Hi

I am having some trouble booting Ubuntu on my MacPro. I have refit installed and also ubuntu installed on a separate internal drive in the mac. The install seems to go o.k and refit sees the installation when I restart ( I get the icon for OSX and an icon for HD installation of Linux). However, when I select the Linux install the screen goes black with a flashing cursor at the top left and all I can do from this point is shut the machine down and turn it back on again.

I have had a look around the forums and can't find anyone who's had this same problem. Any help with this would be very much appreciated.

Also, if I do manage to get it running, how do I install the 64BIT kernel?

Thanx

david

---

### Post by tom4everitt on 2009-12-12
First thing to try is always to sync partition tables. Choose partition tool in the refit menu, and it will most likely ask you to if you want to sync partition tables. Do that. Reboot. And it should probably work. 

When you download ubuntu you can choose either 32 or 64-bit. I don't think its possible to change to a 64-bit kernel after you've installed it actually.

---

### Post by halfloaf on 2009-12-12
> **davidRUK said:**
> Hi

I am having some trouble booting Ubuntu on my MacPro. I have refit installed and also ubuntu installed on a separate internal drive in the mac. The install seems to go o.k and refit sees the installation when I restart ( I get the icon for OSX and an icon for HD installation of Linux). However, when I select the Linux install the screen goes black with a flashing cursor at the top left and all I can do from this point is shut the machine down and turn it back on again.

I have had a look around the forums and can't find anyone who's had this same problem. Any help with this would be very much appreciated.

Also, if I do manage to get it running, how do I install the 64BIT kernel?

Thanx

david

I've had the same problem! I found out I had somehow screwed up my MBR partition and not even rEFIt could fix it.

What I  did was...

* Wiped my linux partitions...
* re-synced my MBR with rEFIt and reboot
* boot into OS X and in a terminal window execute 'fdisk -u "your primary boot drive here"'.
* partition your drive as you want, I used bootcamp
* boot your linux 64bit live cd
* open the partition manager or gparted, erase the bootcamp partition so that you have free space left.
* install to hard drive, make sure you install the boot loader onto your Linux or /boot partition - NOT the MBR!
* Reboot, sync the partition tables with refit's partition tool.
* shut down machine, turn on machine.
* I then removed refit as I didn't like the boot loader, preferring to just hold down the option key while booting.

This worked for me, YMMV.

Jacques

---

### Post by davidRUK on 2009-12-13
Thanks halfloaf, I'll give this a try and get back to you.

David

---

### Post by halfloaf on 2009-12-13
If you ever figure out how to get the Mac Pro to run at a reasonable temperature let me know! Mine runs waay to hot under 9.10 to use it, about 17 degrees C hotter than OS X! Some of my temps go up to 120 degrees C.

-Jacques

---

### Post by davidRUK on 2009-12-13
Hi Jacques

I got it working, thank you for the help. I need to download the new disk though, I'm still on 7.10 lol.

Wow!, thats hot. What software are you running to make it do that?

David

---

### Post by halfloaf on 2009-12-13
No software, just idle!!! If I run a render on Maya using all 8 cores it jumps a further 10 degrees!

Glad you got it working!

---

