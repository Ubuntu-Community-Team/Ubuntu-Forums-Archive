---
title: "No Sound on Mac Book Pro 15&quot;"
date: 2007-03-03
forum: Apple Intel Users
---

### Post by wlarsong on 2007-03-03
After following the instructions extensively at:
[INDENT][http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)[/INDENT]

I am still unable to get the sound working on my Mac Book Pro

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Unknown device 8384:7680
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at 98400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


I have compiled and make installed successfully the latest alsa drivers

alsa-driver-1.0.14rc1

and when i run 

sudo modprobe snd-hda-intel

it appears to work( although I am not sure I run this and hit enter and the terminal waits I have to line kill in order to get back to the terminal ~$)

william@william-laptop:~/src/alsa/alsa-driver-1.0.14rc2$ grep 'audio' /etc/group 
audio:x:29:william

however when i lanuch the alsamixer i get

alsamixer: function snd_ctl_open failed for default: No such device

and

william@william-laptop:~$ strace -eopen alsamixer
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)

alsamixer: function snd_ctl_open failed for default: No such device
Process 5806 detached


and still no sound.

Any Help?

---

### Post by wlarsong on 2007-03-05
I fixed this, after a clean install i imeediatly went into:

alsamixer

and unmuted all the channels and it worked.

---

### Post by Marcel Legros on 2007-12-21
Clean install of Ubuntu from disk, or freshly compiled alsa drivers? I have the exact same laptop and I've tried everything from the MacBookPro wiki pages, to Alsa site, to forums threads - nothing has been successful.

---

### Post by GeneralSunTzu on 2007-12-21
Hello,
I concur, at present there is no way to get sound on a second generation MacBook Pro 15".
MacBook Pro 15" alone means nothing on its own, as the hardware varies greatly among the three (so far) generations of MacBook Pro 15".
No, the recipes for MacBooks will not work for MacBooks Pro and no, what works with a MacBook Pro 17" will not work with a 15".
Also, unlike madwifi, where the latest trunks allows you to use WPA2 PSK on a MBP 15" (I know, am using one right now), no recent alsa software release, trunk or other will work.
So forget it, until next major release of something (alsa, Ubuntu, whatever).

Unfortunate owner of a 2nd generation MBP, like the 1st poster...

---

### Post by Marcel Legros on 2007-12-22
Well, I know it isn't impossible to get sound out of my second generation 15" MBP because after much tinkering and a reboot this morning, sound began blaring from my speakers. Unfortunately, the X server no longer functioned properly and only displayed a blank white screen. Oddly, compiz was still operating and I could rotate 4 blank desktops on the cube! In the end I couldn't figure out how to restore my video and had to reinstall gutsy from scratch - again. I'm determined to find an answer. When I do, I'll post the steps for others to follow.

The guide on the MBP wiki was not sufficient to get sound working for me.
[B]
EDIT:[/B] I got it working, using this excellent post [http://ubuntuforums.org/showthread.php?p=3996120#post3996120](http://ubuntuforums.org/showthread.php?p=3996120#post3996120)
You have to compile new ALSA drivers using the module-assistant instructions. All works, including headphones and mic. YAY!

---

### Post by GeneralSunTzu on 2007-12-23
> **Marcel Legros said:**
> Well, I know it isn't impossible to get sound out of my second generation 15" MBP because after much tinkering and a reboot this morning, sound began blaring from my speakers. Unfortunately, the X server no longer functioned properly and only displayed a blank white screen. Oddly, compiz was still operating and I could rotate 4 blank desktops on the cube! In the end I couldn't figure out how to restore my video and had to reinstall gutsy from scratch - again. I'm determined to find an answer. When I do, I'll post the steps for others to follow.

The guide on the MBP wiki was not sufficient to get sound working for me.
[B]
EDIT:[/B] I got it working, using this excellent post [http://ubuntuforums.org/showthread.php?p=3996120#post3996120](http://ubuntuforums.org/showthread.php?p=3996120#post3996120)
You have to compile new ALSA drivers using the module-assistant instructions. All works, including headphones and mic. YAY!


Thank you for reporting success. I am unable to do so.
Do you also have a Sigmatel sound card (as listed by lspci -v)? If so, ALSA has no driver for it...

---

### Post by rvm1989 on 2008-03-15
alsa has a new version the 1.0.16 with this one my sound works perfect on my macbook pro 15" second edition

to install download the new drivers from the website.
[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
           (you only need the firt one, the alsa driver)
unpack this in your home directory
and then use following commands:
```

cd alsa-driver [TAB - to fill in the correct numbers]
./hgcompile
make
sudo make install

sudo /etc/init.d/alsasound stop
sudo lsmod [verify all snd modules are unloaded]

sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo depmod -a

sudo modprobe snd-hda-intel

```
Press Ctrl+Alt+Backspace to restart gdm.

From here you'll need to run alsamixer to unmute the Master, PCM, Line Out, and apply the settings described before.

Note that you'll probably need to recompile after every kernel upgrade.

---

### Post by GeneralSunTzu on 2008-03-16
Thank you so very much rvm1989.
Your instructions worked and were very detailed.
Recompiling alsamixer is not a problem, as I am already obliged to recompile madwifi (NOT the last version) every time there is a kernel upgrade.
Let's see whether HH brings us some improvements, both in the WiFi connectivity and the sound area.

PS I did not need to unmute anything, but probably I had unmuted it during one of my previous unfortunate attempts to get sound to work.

---

### Post by RonakG on 2008-06-28
I have tried almost everything available to enable sound on my MBP 4th edition. But nothing works.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 00a3
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

---

### Post by cyberdork33 on 2008-07-02
Please post in the new forum. This one is now just an archive.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

