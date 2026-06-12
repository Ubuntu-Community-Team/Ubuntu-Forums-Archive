---
title: "Desktop Effects working in jaunty on ppc?"
date: 2009-04-19
forum: Apple Hardware Users
---

### Post by spydouglas on 2009-04-19
I've recently installed jaunty (beta, now release candidate) on my Powerbook G4 5,8 and have been impressed by some things, but disappointed that desktop effects no longer work.  Has anyone else tested desktop effects/DRI on PPC jaunty?  My video card is an rv350 (mobility radeon 9600).

---

### Post by albertone on 2009-04-21
Same probleme for me with a G4 2 x 1,2 Ghz PPC
Compiz worked fine with Ubuntu 8.10 but no more with jaunty
Here are the result of 
:~$ lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

too bad :(

---

### Post by joshdudeha on 2009-04-21
Mine don't work, but it's an nVidia, which I believe don't work terribly well on PPC Ubuntu

---

### Post by spydouglas on 2009-04-22
Thanks for the feedback.  Have either of you filed a bug?  A compiz developer told me that my bug ([https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/359839]("https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/359839")) was actually not a compiz bug, but a kernel bug.

---

### Post by joshdudeha on 2009-04-23
I think the reason why mine don't work is because nVidia won't release their proprietary drivers to Power PC Linux. Making it hard for the programmers to make a decent driver.
Which basically means you can't use Compiz or anything like that if you have a Nvidia Power PC Computer.. like me.

I doubt there'll be any support for it, as power pc apple is an old platform now and people are focusing on new technology

---

### Post by fraterf93 on 2009-04-24
On my Mac mini, and my iMac G4 I have the same problem.  Desktop effects worked before the upgrade, after the upgrade they no longer work.  I should have expected this as over the years this is a running theme for us Mac PPC users when upgrading.  Things that previously worked get broken  :(

---

### Post by spydouglas on 2009-04-24
That's sad, but understandable, as ppc's slowly die off...

The problem in my case apparently is that the drm kernel module cannot initialize my radeon card properly.  If anyone who's posted has a chance, could you check your dmesg to see if the output is similar?  The crucial line appears to be:

[   31.423017] [drm:radeon_do_init_cp] *ERROR* could not find ioremap agp regions!

which appears as the last line in my dmesg output.  Just in case you don't know how to find this, typing 'dmseg | grep ioremap' (without the quotes) in a terminal window should find it. (If nothing shows up, then this line doesn't exist in your dmesg.)

---

### Post by albertone on 2009-04-29
here it is 


[   27.694188] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   27.978584] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 4x mode
[   27.978599] radeonfb 0000:00:10.0: putting AGP V2 device into 4x mode
[   28.000331] lp: driver loaded but no devices found
[   28.027416] ppdev: user-space parallel port driver
[   28.249168] __ioremap(): phys addr 0x0 is RAM lr f29ea01c
[   28.249180] __ioremap(): phys addr 0x101000 is RAM lr f29ea01c
[   28.249184] __ioremap(): phys addr 0x102000 is RAM lr f29ea01c
[   28.249189] [drm:radeon_do_init_cp] *ERROR* could not find ioremap agp region

---

### Post by spydouglas on 2009-05-03
albertone, could you mark the bug as confirmed?  I would do so myself, but I'm not sure if that's proper procedure.

---

### Post by ramenite on 2009-05-04
I posted a thread about this.

It is a bug in the DRI module. You can compile your own kernel, and things work fine. I have an iBook G4 with a Radeon 9200 Mobility. I'm using Compiz, and other 3D applications.

---

### Post by spydouglas on 2009-05-04
That's good to know.  What needs to be changed from the default kernel build to get it to work?

[Edit: I found your post that describes the workaround: [http://ubuntuforums.org/showthread.php?t=1145849]("http://ubuntuforums.org/showthread.php?t=1145849")]

---

### Post by ramenite on 2009-05-04
> **spydouglas said:**
> That's good to know.  What needs to be changed from the default kernel build to get it to work?

[Edit: I found your post that describes the workaround: [http://ubuntuforums.org/showthread.php?t=1145849]("http://ubuntuforums.org/showthread.php?t=1145849")]

Yes, I didn't change a thing--just copied the old config to the new kernel.

---

### Post by spydouglas on 2009-05-04
> **ramenite said:**
> Yes, I didn't change a thing--just copied the old config to the new kernel.

I'm happy to report that it works with such a configuration, as I'm running it now!  

One thing that I should mention to other readers that wasn't clear to me at first is that you must compile a vanilla kernel (i.e. from kernel.org), as ubuntu patches cause the bug.

---

### Post by albertone on 2009-05-07
thanks a lot !
I miss the compiz effect so much. It's will be my first kernel compilation but i'll try this week-end (with the old  kernel configuration, of course) and i'll post the result here :)

---

### Post by spydouglas on 2009-05-07
One side-effect I've discovered in the past few days is that after suspend/restoring my laptop, desktop effects have to be restarted manually.  I'm currently running kubuntu, which uses a different compositor; it may be different for gnome/compiz.  If you're running a laptop, let me know if you experience this as well.

---

### Post by spydouglas on 2009-05-07
Another bug filed on this issue ([https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/345542/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/345542/comments/22)) suggests using the radeon card as a PCI device as a less drastic workaround.  It only requires editing xorg.conf, rather than compiling a new kernel.  

[Edit: So far, this workaround works!]

---

### Post by albertone on 2009-05-08
to compile a new kernel is not working for me.
I have just installed kernel 2.6.29.2 from kernel.org (with the old .config) and compiz always don't want to work.

The solution with "Option "BusType" "PCI"" in xorg.conf don't bring, in my case, more success.

My mac is a G4 2 x 1,2 Ghz PPC with a graphic card
ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

Shall I try with an older kernel ?

---

### Post by albertone on 2009-05-09
yes, now compiz work   :P
i read somewhere that all effect are working on 9.04 PPC with KDE.
So, I  have just installed KDE on my Mac, and surprise,
effect are working, so I went back to Gnome session and Big Surprise they are working too now :P:P

Thanks a lot to everyone who helped and long life to Linux, Ubuntu and Free Software. 


:lolflag:

Sorry, for my (too) bad english

---

### Post by spydouglas on 2009-05-09
> **albertone said:**
> yes, now compiz work   :P
i read somewhere that all effect are working on 9.04 PPC with KDE.
So, I  have just installed KDE on my Mac, and surprise,
effect are working, so I went back to Gnome session and Big Surprise they are working too now :P:P


What configuration ended up working?  Did you have to change any settings to get desktop effects working in KDE?  (I'm running KDE and nothing would work until I edited xorg.conf.)

---

### Post by lethrj on 2009-05-15
> **spydouglas said:**
> I've recently installed jaunty (beta, now release candidate) on my Powerbook G4 5,8 and have been impressed by some things, but disappointed that desktop effects no longer work.  Has anyone else tested desktop effects/DRI on PPC jaunty?  My video card is an rv350 (mobility radeon 9600).

I've got the same setup.  Same problems too.
I have done this stuff, and seen limited success.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I have gone back to "None" effects because of frequent freezes while doing trivial things, like alt+tab application switching, using either "Normal" or "Extra."  Has anyone come up with driver and xorg.conf settings that give acceptable performance?

---

### Post by stream303 on 2009-05-15
I seem to remember those cards having problems with desktop affects back in the old driver days when using the default 24-bit color depth.

Can you edit your /etc/X11/xorg.conf, and force it to 16-bits instead?  This might be the tradeoff to get it to work if 16-bit color depth is usable for you.

Ie, something like this:

```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        **DefaultDepth 16**
        SubSection "Display"
                Viewport  0 0
                **Depth     16**
                Modes     "1024x768"
        EndSubSection
EndSection
```

---

### Post by Shazz.ng on 2009-05-18
I had the same issue with my mac mini 1.42Ghz/RV280, I tried the PCI workaround but with very limited success too (about 500 FPs but a very glitchy display).

So I have upgraded the kernel to 2.6.29.3 (not so difficult, I never did it before and I did not face any issue, thanks to the very good tutorial found on this forum) and the problem disappeared.

Now that's about 1250 FPs. I thought it should be better but that's enough for OpenGL screensavers, games and Compiz desktop effects.

---

### Post by staticdisaster on 2009-05-18
anybody have any idea when they're going to upload a new kernel deb file .. or maybe someone can post their own linux kernel .deb file? even with that PCI option in xorg.conf, my desktop feels so slow ...

---

### Post by Shazz.ng on 2009-05-18
if it can help.....
[http://tmpstore.free.fr/ubuntuppc/](http://tmpstore.free.fr/ubuntuppc/)

kernel 2.6.29.3 recompiled with my existing config file, no special optimizations.

---

