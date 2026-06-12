---
title: "Hoary on a powerbook5,6: what works and not"
date: 2005-05-13
forum: Apple PPC Users
---

### Post by johj on 2005-05-13
I recently bought a brand new PowerBook G4 15'' 1.67GHz with SuperDrive (a powerbook5,6). My plan was to run Ubuntu on it. Here are my experiences:

**Installation**
Installation went fine without any problems. Remember to use the standard ethernet port for internet access, as Airport Extreme does not work (more below).

**What works**

[list]
[*]CPU - MPC7447A CPU 1.67GHz (needs kernel patch to run at full speed)
[*]IDE hard drive
[*]Ethernet controller (Sun GEM)
[*]USB
[*]Bluetooth
[*]PCMCIA (I think)
[*]Trackpad (with experimental driver)
[*]Temperature/fan control (needs kernel patch)
[*]Battery status
[*]Sound (needs kernel patch)
[*]Firewire (reported to work, haven't tested)
[/list]
**Kernel patches**
I currently run a 2.6.11.8 kernel with the following patches:
cpufreq.patch: to make the CPU run on full speed.
therm.patch: to make the temperature sensor work.
fnkey.patch: to make the fn-key work.
sound.patch: to make the sound system working.

All these patches can be found on Jochen Voss' excellent powerbook webpage at [http://seehuhn.de/comp/powerbook/index#kernel](http://seehuhn.de/comp/powerbook/index#kernel). Let me know if you want my pre-compiled kernel debian package (with headers).

**Trackpad/touchpad**
The trackpad does not work out of the box, but with Johannes Berg's experimental [touchpad driver](http://johannes.sipsolutions.net/PowerBook/touchpad/driver) it somewhat works. It is extremely sensitive, making the mouse pointer bounce around. Setting the THRESHOLD to about 35-40 in the userspace daemon (driver.c), it gets less bouncy but it makes the trackpad less sensitive. I.e. you must press harder to get any reaction. It's interesting though, if you leave the THRESHOLD on 20, you can actually hold your hand **above** the touchpad and see the pointer bounce around! Pretty sensitive hardware!

**Keyboard**
As you might already know, the keyboards that come with Macs are far from UNIX-firendly. Jochen Voss has made some [key bindings for British (gb) and German (de) models](http://seehuhn.de/comp/powerbook/index#keyboard) (requires fnkey kernel patch). I modified the British version and made a new XKB symbol map for my Norwegian keyboard. Let me know if you're interested in it.

**Special keys**
There's a lot of special keys on the powerbook. There are keys for:
[list]
[*]LCD brightness
[*]Volume control
[*]Num lock
[*]External display
[*]Keyboard illumination
[*]Eject
[/list]

I haven't gotten any of these keys to send a different keycode than the function keys they're on. Therefore, I'm using control as the modifier for these buttons. Making them work requires [pbbuttonsd](http://pbbuttons.sourceforge.net/), which also deals with the power management. It requires some tweaking to work though, but I've managed to get it working pretty nicely. I stumbled into one problem though: closing the cover. When running pbbuttonsd with a default config, closing the cover first blanked the screen for a second, then turned it on again! Now, when opening the cover again, the screen goes blank! Now this is handy! I found that setting the configuration entry UseFBBlank to "no" fixed the problem.

The eject button works, but it won't eject any cd that is still mounted. Unmounting the cd and then pressing eject works, but I find it a bit faster just to right-click on the cd and choose "eject" :P

I haven't gotten the keyboard illumination nor the light-sensors to work yet though. If anyone got this working, please let me know!

The power button also doesn't work, though Johannes Berg at his site has a patch for pbbuttonsd making this work. I haven't tried it yet though.

**What works not**

**Airpot Extreme**
This is unlikely to get supported in the near future, but there's an interesting project going on which aims to reverse engineer the BCM4301 chipset at [http://linux-bcom4301.sourceforge.net/](http://linux-bcom4301.sourceforge.net/)
There's also a petition going on with loads of signatures, but it doesn't seem Broadcom is paying any attention to it.

Therefore, I've ordered a wireless PCMCIA card instead. I guess this is the only way to get wireless working at this point.

**3D acceleration**
3D acceleration (ATI RV350 [Mobility Radeon 9600 M10]) is not supported. ATI haven't (and are not planning to as far as I know) released any drivers for this card for the powerpc architecture.

**Sleep/suspend**
I haven't got sleep nor suspend to work. This is really annoying. When starting the pmud daemon, it outputs this to the system log:
May 13 15:48:43 FarBook pmud[7530]: pmud [treshold = 420, margin = 15] started
May 13 15:48:43 FarBook pmud[7530]: PMU version 12: iBook/G3 Pismo/G4 Titanium
May 13 15:48:43 FarBook pmud[7530]: No sleep support on this hardware, exiting!
May 13 15:48:43 FarBook pmud[7530]: daemon stopped (missing sleep support)

If **anyone** has gotten sleep or suspend to work on the powerbook5,6, please let me know!

**Other problems**
I've had some problems mounting HFS+ filesystems. It seems that if they're not umounted properly, they won't mount rw. The only thing I've found that fixes this, is to boot into MacOS X and repair the disk using the Disk Utility.


**Links**
These webpages has helped me a lot:
[Linux on an Apple Powerbook G4](http://seehuhn.de/comp/powerbook/index)
[Johannes Berg's PowerBook page](http://johannes.sipsolutions.net/PowerBook)

As you can see, there are quite a few problems when running linux on a powerbook. Nevertheless, it's pretty cool!

Please let me know if there's anything you've gotten working which I haven't (or vice versa)... ;)

---

### Post by flim on 2005-05-23
Hi,
very good post - I had fun reading it and took some knowledge from it. However, I wasn't able to apply the sound patch myself (I did, but it somehow doesn't work out, still no sound on new kernel). Could you explain how you did that and maybe supply your kernel?
I'm actually not running a 5,6 powerbook, but a 5,7(new 17") and am not sure if that makes any difference. Couldn't find any info on that as well.

Thanks,
flim

---

### Post by johj on 2005-05-24
Hello, I'm glad that you found my post useful!

I applied the patch to a pristine linux-2.6.11.8 kernel as usual with
```
$ patch -p1 < 010-sound.patch
```

After that, sound worked. You need to fiddle with the mixer settings to get it sound right though. I had to turn down the PCM to about 80 to get sound with decent quality (i.e. without fuzz).

The cpufreq, therm and sound patches are all applied to the 2.6.12-rc4 kernel.
Also, sleep (suspend-to-ram) is also supported in this kernel! :D

I'm currently running a 2.6.12-rc4 kernel with the fnkey patch applied. I'm having some problems with the fnkey behaving strangely (need to hold down for example the home/end key for some time before it actually responds with the home/end behaviour. I don't know what's causing this, but there were some problems applying the fnkey patch to the 2.6.12-rc4 kernel (I know it's not meant for it anyways). I will investigate).

As for the kernel, I'm planning to put up a webpage and a repository with kernel configuration, kernel packages, etc. I'll post here when it's up.

---

### Post by flim on 2005-05-24
Hm, that kernel you mentioned is not available in repositories, is it? I'm not really familiar with the way debian based stuff works, but somehow there's something in my mind about debian specific patches I'd have to apply as well if I get a 'normal' kernel? Stupid question maybe - I'm just confused right now and a little bit lost. I haven't been compiling kernels since a loooong time and had to find out that I lost all knowledge I might have had in the past:| Some of it still feels right, but other stuff just leaves me behind. In order to get that compile working I used the currently available kernel version from repository (can't look that up know, working on rpm based distro) and followed some tutorial to get the work done (which wasn't really a lot - comes down to 4 commands or something like that).

cheers
flim

---

### Post by johj on 2005-05-24
I've put up a page with information (more or less what's in this post) and files including kernel packages, patches, etc. on [http://joh.deworks.net/powerbook](http://joh.deworks.net/powerbook).

---

### Post by johj on 2005-05-24
[QUOTE=flim]Hm, that kernel you mentioned is not available in repositories, is it? I'm not really familiar with the way debian based stuff works, but somehow there's something in my mind about debian specific patches I'd have to apply as well if I get a 'normal' kernel? Stupid question maybe - I'm just confused right now and a little bit lost. I haven't been compiling kernels since a loooong time and had to find out that I lost all knowledge I might have had in the past:| Some of it still feels right, but other stuff just leaves me behind. In order to get that compile working I used the currently available kernel version from repository (can't look that up know, working on rpm based distro) and followed some tutorial to get the work done (which wasn't really a lot - comes down to 4 commands or something like that).

cheers
flim[/QUOTE]
 The kernel I mentioned I got from the kernel repositories at kernel.org. You can download it from my powerbook page also.

---

### Post by flim on 2005-05-24
Hi,
just tested out your kernel - didn't really work out for me. Next to a couple of error messages concerning hardware that doesn't exist on boot sound did still not work. I getting to believe that it must actually be the 17" powerbook itself somehow not supporting the patch - maybe the hardware is different. Actually, before you applied the patch, how did your mixer look like? I mean, it's just showing 'internal speakers' all the time, which is true but it sounds like this beep things in normal pcs. Besides that there's nothing - only adjustment for internal speaker and beep (which of course both don't work).
But the page is good work - I'll try to compile that new kernel myself over night, maybe that helps.

I must say that you've been helping a lot and am appreciating that a lot - sorry for not being able to pay that back:|

cheers
flim

---

### Post by johj on 2005-05-26
I'm sorry the kernel didn't work out for you... Which kernel did you try? 2.6.11.8 or 2.6.12-rc4? I don't know about the sound card on the 17" models. Maybe it's different? Before compiling your own kernel, I would suggest trying the 2.6.12-rc4 kernel.

Hope it works!

---

### Post by flim on 2005-05-26
Well, I tested both kernels on your site and patched/compiled different kernel myself various times.
I wasn't able to find any information about the soundcard of 15" or 17" models apart from what's on apples page - so there might very well be a difference. Still, as I haven't done this kind of stuff in a while I guess that I've just missed some configuration settings apart from the kernel. Did sound work right out of the box for you after installing the new kernel? Or have there been any extra configuration changes you had to do?

Cheers
flim

---

### Post by open_flax on 2005-05-26
Hello

 if you need a sleep function you can see this post:
[http://ubuntuforums.org/showthread.php?t=33766&highlight=sleep](http://ubuntuforums.org/showthread.php?t=33766&highlight=sleep)

---

