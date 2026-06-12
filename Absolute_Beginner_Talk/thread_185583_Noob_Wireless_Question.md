---
title: "Noob Wireless Question"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by snorlax on 2006-05-31
Hi...Have my Ubuntu 5.10 running smoothly except for wireless networking.
From the looks of the posts and other traffic, I'm not alone.

I have a Belkin USB wireless stick and found instructions for installing it here:

[http://opensource.bureau-cornavin.com/belkin/](http://opensource.bureau-cornavin.com/belkin/)

This stick has served me well on both Win98se and XP

Since Ubuntu does not support this USB stick natively, I could only use NDISWRAPPER and followed the instructions for my chipset, Zydas 1211B.

I got through the ndiswrapper stuff and the modprobe ok, but wlan0 never showed up.

If I go through NDISWRAPPER to install the USB wireless stick, should [COLOR="Red"]linux-wlan-ng[/COLOR] be installed or uninstalled?

I also noticed that one form of this attempted installation hosed my X-server...the system either went to a control prompt because X failed, or, after I changed some settings, the keyboard would act erratically.

Everything else on this installation is excellent.  BTW, it is an old pentium II laptop.

In trying to help myself, I also noticed that there seems to be a fair amount of contradictory info out there.  

I tried to install another USB wireless stick (Netgear MA111) and tried to follow advice I found in several places...some of it said that I needed the Prism driver and other info said to remove it because it conflicted with ndiswrapper.  Neither situation worked ](*,) 

My first choice is to install the Belkin stick, as the Netgear stick belongs to another computer.  As I say, the Belkin worked fine on this computer under 98se and on another under XP pro.

Does the new 6.0.6 make USB Wireless any easier?  More native support perchance??

I turn to the experts for advice:) 
Thanx in advance...

Jim "snorlax" Williams

---

### Post by nalmeth on 2006-06-01
I've heard that 6.06 has resolved wireless issues for some. It didn't help me, though I think I've narrowed my wireless problem down to... well I won't get into it.

The Wireless Help guide in my signature is the next best advice I can give, if you haven't been there already.

---

### Post by Travisty on 2006-06-01
Jim,

What was the output of [COLOR="Red"]ndiswrapper -l[/COLOR] with the belikin USB device. If you followed the steps from the available posts online you should have come across this step [COLOR="#ff0000"]dmesg | grep ndiswrapper[/COLOR], what was the output from that?

---

### Post by snorlax on 2006-06-01
[QUOTE=Travisty]Jim,

What was the output of [COLOR="Red"]ndiswrapper -l[/COLOR] with the belikin USB device. If you followed the steps from the available posts online you should have come across this step [COLOR="#ff0000"]dmesg | grep ndiswrapper[/COLOR], what was the output from that?[/QUOTE]

Hi, and thanx for taking time to help!

[COLOR="Red"]This is all with linux-wlan-ng uninstalled.[/COLOR]


======================================================

ndiswrapper -l yields driver present, hardware present. That's good, yes?:) 

right now, dmesg | grep ndiswrapper yields NOTHING AT ALL. That's bad, yes?

network setting shows ONLY PPP0, no mention of wlan0

/etc/network/interfaces has only a comment from me with # and a space before it, then iface wlan0 inet dhcp  (and the lo entry before that).

/etc/modprobe.d/ndiswrapper shows alias wlan0 ndiswrapper

/etc/ndiswrapper/blkwgu has the .inf and .sys files I copied from the belkin disk and "ndiswrappered," plus a config file that I assume was created from the XP .inf and .sys files.  Blkwgu is the name of the .inf file.

Thanx for any insight you may have!!

Jim

---

### Post by Travisty on 2006-06-01
It's good to see that the driver and hardware are present.

If you do [COLOR="Red"]modprobe ndiswrapper[/COLOR] followed by [COLOR="Red"]dmesg | grep ndiswrapper[/COLOR] then you should have an out put like this (if everything is OK):
diswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
    ndiswrapper: driver net111v2 (NETGEAR Inc.,03/24/2005,5.111.05.0324) added

If it's not working then it looks more like this:
[ 58.402186] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[ 58.447947] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit; bad magic: 010B
[ 58.447952] ndiswrapper (load_sys_files:21: couldn't prepare driver 'netwg111'
[ 58.448344] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[ 58.448348] ndiswrapper: probe of 2-8:1.0 failed with error -22
[ 58.448359] usbcore: registered new driver ndiswrapper

---

### Post by snorlax on 2006-06-01
> **Travisty]It's good to see that the driver and hardware are present.

If you do [COLOR="Red"]modprobe ndiswrapper[/COLOR] followed by [COLOR="Red"]dmesg | grep ndiswrapper[/COLOR] then you should have an out put like this (if everything is OK):
diswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
    ndiswrapper: driver net111v2 (NETGEAR Inc.,03/24/2005,5.111.05.0324) added

If it's not working then it looks more like this:
[ 58.402186] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[ 58.447947] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit said:**
>  ndiswrapper (load_sys_files:21: couldn't prepare driver 'netwg111'
[ 58.448344] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[ 58.448348] ndiswrapper: probe of 2-8:1.0 failed with error -22
[ 58.448359] usbcore: registered new driver ndiswrapper

WOW! I got nothing...any idea why?

And while we're at it,I have an MA111 version 1.  I've seen a zillion ways to make that work, but I couldn't get any of 'em to go for me.
Given that I'm still new at this, would you recommend upgrading now to the 6.0.6 or waiting until I am more skilled with the 5.10?
Thanx...Jim

---

### Post by Travisty on 2006-06-02
Being a dapper user I would say upgrade :) but that is completly up to you. There have been alot of possitve changes from 5.10 but there is absolutally nothing wrong with the version you currently have so again up to you.

Did Linux recognize the Wireless device before you started playing around with Ndis wrapper (did it assign it as eth or a wlan)?

---

### Post by snorlax on 2006-06-02
[QUOTE=Travisty]Being a dapper user I would say upgrade :) but that is completly up to you. There have been alot of possitve changes from 5.10 but there is absolutally nothing wrong with the version you currently have so again up to you.

Did Linux recognize the Wireless device before you started playing around with Ndis wrapper (did it assign it as eth or a wlan)?[/QUOTE]

Well, I may do that since I'm so new...

The system did not pick up the device natively.  The site I looked at gave several alternatives & the one that fit me, unfortunately, was the ndis wrapper solution.

Does the use of ndiswrapper mean that I should uninstall linux-wlan-ng?

Thanx,
Jim

---

