---
title: "Matrox G400 graphics card, not sure it's working."
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by BackInTimeMan on 2006-09-18
Hi,

I have a Matrox G400 graphics card but am not sure that it's working. Why? Apart from the fact that it doesn't show up in Device Manager, it's just a feeling. I'm running on a Pentium 111 (Coppermine) with 512 MB RAM and until I entered the correct sync rates for my moniter in xorg.conf, the  screen resolution was 800x600 with a 60 Hz refresh rate. If I grabbed a window by the title bar and *shook* it a bit, the edges of the window went blurred and smeared. After entering the correct sync rates and choosing 1024x768 screen resolution with a 70 Hz refresh rate, that effect is much reduced but still there a bit.

If I do a "lspci" command, the Matrox card is identified:

0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 04)

As it is with the "lshw" command:

*-display
                description: VGA compatible controller
                product: G400/G450
                vendor: Matrox Graphics, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 04
                size: 32MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=matrox_w1
                resources: iomemory:d8000000-d9ffffff iomemory:d4000000-d4003fff iomemory:d5000000-d57fffff irq:11

My xorg.conf looks in order:

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA G400 AGP"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Option		"OldDmaInit"		"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-58
	VertRefresh	50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G400 AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24

I already altered the "Monitor" section to give the correct sync rates for my monitor, so far so good...

But, in Device Manager, the Matrox card is not listed.

Searching my file system for "Matrox" gives this result:

/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/i2c-matroxfb.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_DAC1064.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_Ti3026.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_accel.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_base.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_crtc2.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_g450.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_maven.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/matrox/matroxfb_misc.ko
/lib/modules/2.6.15-26-386/kernel/drivers/w1/matrox_w1.ko

That seems to indicate there are Matrox drivers already installed, and the driver entry (matrox_w1) coincides with the entry for my graphics card driver in the "lshw" listing. I found a new driver at the Matrox site and tried to install it, but the path it wanted to install to doesn't exist. I didn't want to put the new driver files in the existing Matrox folder until I find out why the drivers that are already there are not being used.

So, my first question is, how can I get the card to show up in Device Manager?

I found some threads that mention Matrox cards but they seemed mainly to be focusing on the dual screen aspect. Mine is dual screen capable but that's not what I want to do ATM. I did see mention of the mgapdesk utility though and thought that may be worth a shot so I tried to install it:

sudo aptitude install mgapdesk
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  mgapdesk
The following NEW packages will be automatically installed:
  libglib1.2 libgtk1.2 libgtk1.2-common
The following NEW packages will be installed:
  libglib1.2 libgtk1.2 libgtk1.2-common
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 861kB/1972kB of archives. After unpacking 5841kB will be used.
The following packages have unmet dependencies:
  mgapdesk: Depends: xserver-xfree86 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mgapdesk [Not Installed]

Score is 1

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

This is puzzling to me. It seemed to install four packages that mgapdesk needed, then said it had unmet dependencies, namely, xserver-xfree8 which I thought was already installed. Next it says it will resolve the dependencies, then doesn't installl mgapdesk! I agreed to accept so as to finish the process.

So my second question is, what happened here?, why didn't mgapdesk get installed?

Any clue-giving will be gratefully received!

---

### Post by BackInTimeMan on 2006-09-19
Well, I don't know how many times I looked and couldn't find my card listed in Device Manager, but now I see it! Guess it is being used after all.

I would still like to know why mgapdesk didn't get installed though if anyone can help me there.

---

### Post by SammyBoy247 on 2006-09-22
I have exactly the same problem have you got any further?  I am have screensaver problems causing my system to crash and I think it's down to the Matrox.

---

### Post by Omnios on 2006-09-22
This is the wiki page on the graphics card.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28G400%29%7C%28Matrox%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28G400%29%7C%28Matrox%29)

[https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia)

---

### Post by BackInTimeMan on 2006-10-09
> **SammyBoy247 said:**
> I have exactly the same problem have you got any further?  I am have screensaver problems causing my system to crash and I think it's down to the Matrox.

Sorry to take so long to reply, somehow I didn't see the reply's to my post.

Any further with mgapdesk?, no. I tried again to install it and now get a slightly different message:

```
 sudo aptitude install mgapdesk
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  mgapdesk
The following packages have been kept back:
  cpio libmono0 libssl0.9.8 mono-classlib-1.0 mono-common mono-jit openssl
  python2.4 python2.4-examples python2.4-gdbm python2.4-minimal
  python2.4-tk xorg-edit
0 packages upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 861kB of archives. After unpacking 2793kB will be used.
The following packages have unmet dependencies:
  mgapdesk: Depends: xserver-xfree86 which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

I'm puzzled about the mention of xserver-xfree86 which I thought was already installed. If I try to install it I get this:

 ```
sudo aptitude install xserver-xfree86
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for xserver-xfree86
The following packages have been kept back:
  cpio libmono0 libssl0.9.8 mono-classlib-1.0 mono-common mono-jit openssl
  python2.4 python2.4-examples python2.4-gdbm python2.4-minimal
  python2.4-tk xorg-edit
0 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

So, no good so far...  :???:

As I mentioned, I found that my card is being used but I'm still getting a smeer effect if I shake a wimdow about. Maybe I just haven't got enough memory installed for Ubuntu, it's OK with XP though.

I found an updated driver on the MAtrox site and tried to install it but the path it wants to install to doesn't exist.

I'd be interested to know if you manage to install mgapdesk  :)

---

### Post by BackInTimeMan on 2006-10-09
> **Omnios said:**
> This is the wiki page on the graphics card.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28G400%29%7C%28Matrox%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28G400%29%7C%28Matrox%29)

[https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia)

Thanks for the links, I'll check them out.

And sorry for the delay in responding.

---

### Post by Jasper84 on 2006-10-15
I just fixed my graphics card problems (got hardware accel now :D) But sudo aptitude install mgapdesk worked for me. (so cant help there)
Maybe you can manually alter /etc/X11/xorg.conf after backing it up. Dunno whether that's smart, sounds a bit risky.
from
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28G400%29%7C%28Matrox%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28G400%29%7C%28Matrox%29)
it says "3D works in 16 bit mode" so will need to set some number 32 or 24 (8?) to 16. (mgapdesk did that in my case)
Looking at my altered(by mgapdesk) and backup .conf it seems it changed after Section "Screen" DefaultDepth from 24 to 16 so doing that manually may fix your problem. It may have changed some other bits too, so attached are both files. (btw these files may be different in other places for your computer, don't just copy!)

DO NOTE that it is all at your own risk, backup the .conf file. (if it breaks ubuntu you can try fix it with a live cd that can read the harddisk (reverting to old .conf file))

I hope Dapper Drake fixes this issue, i am using Breezy. (maybe i should check)

---

### Post by BackInTimeMan on 2006-10-15
Jasper84,

I had looked at the linked page but for some reason had not altered my default depth to 16 bit. Just done that and now I have hardware acceleration! Thanks for the nudge!  :D

I still cannot get mgapdesk to install though, it wants xserver-xfree86, which also won't install. Maybe I need to install it manually, more research needed on that. BTW, I'm using Dapper.

Thanks :)

---

### Post by karip on 2006-10-27
I also had the problem of the windows smearing in Dapper when moving them around with *one individual* of these cards. This was due to the card chip overheating. The problem disappeared after installing a cooler onto the chip.

Kari

---

### Post by karip on 2006-10-27
I meant to say I installed a fan onto the cooler.

---

### Post by BackInTimeMan on 2006-10-30
> **karip said:**
> I also had the problem of the windows smearing in Dapper when moving them around with *one individual* of these cards. This was due to the card chip overheating. The problem disappeared after installing a cooler onto the chip.

Kari

Hmm, my card chip doesn't appear to be overheating and it's still happening now that I've upgraded to Edgy.

---

