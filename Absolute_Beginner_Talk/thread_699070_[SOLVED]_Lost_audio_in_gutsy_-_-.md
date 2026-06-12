---
title: "[SOLVED] Lost audio in gutsy -_-"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-02-17
nothing will work!, ive tried the command line, adjusting the settings, but i cant get my sound to work anymore, and i know its a Ubuntu thing because the sound works fine on my vista partition, it used to work on Ubuntu, not anymore though.

Ubuntu 7.10 AMD64 turion

---

### Post by quanumphaze on 2008-02-17
Firstly you need to find out what audio card you have. Type in a terminal:```
lspci -v
```
This will give a long list of your hardware. Somewhere above is the audio.
Look for "Audio device" or similar.

Come back with the results.

Also try this if you want.
[Comprehensive Sound Problem Solutions Guide - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Jerad on 2008-02-17
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


my sound is also not working...

and my wireless internet isn't working either...

i had everything working great with 7.04 then i was bored so i upgraded to 7.10 and now no sound or wireless internet...

please help so i can continue to enjoy ubuntu...:D

---

### Post by linksolo74 on 2008-02-17
Sorry if you already tried this, but i had the same problem a few weeks ago. I fixed it by double clicking on the speaker icon on the menu bar and raising the PCM.

---

### Post by chips24 on 2008-02-17
its an Alsa Nvidia mixer, i will have to restart my computer to do those commands... 


Ill Be Back   :guitar:

---

### Post by Presto123 on 2008-02-17
> **Jerad said:**
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


my sound is also not working...

and my wireless internet isn't working either...

i had everything working great with 7.04 then i was bored so i upgraded to 7.10 and now no sound or wireless internet...

please help so i can continue to enjoy ubuntu...:D

I have the same card...I would suggest checking in System/Preferences/Sound and selecting ALSA. Use the test tone, and if it doesn't work, try the other sound drivers that are listed.

---

### Post by Presto123 on 2008-02-17
Let me also add that, with Vista, you need to shut down the computer before getting into Ubuntu. For some reason, Vista does not release the driver until a full shut-down.

---

### Post by chips24 on 2008-02-17
ok, nVidia Corporation McP51 High Definition Audio  (rec a2)

66MHz

---

### Post by chips24 on 2008-02-17
there was only one other sound driver,and it didnt work either

---

### Post by quanumphaze on 2008-02-17
I have the Intel HDA and it was a real PITA to get working.

If you are lucky you just have to reinstall or reconfigure ALSA. Or if like me you may need to compile ALSA from source.
Please note that it's not that intimidating to compile from source. I did it on my 2nd day of Ubuntu. Involved mostly copy and paste in the terminal.

---

### Post by chips24 on 2008-02-17
> **Jerad said:**
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


my sound is also not working...

and my wireless internet isn't working either...

i had everything working great with 7.04 then i was bored so i upgraded to 7.10 and now no sound or wireless internet...

please help so i can continue to enjoy ubuntu...:D

i dont think ive ever actually enjoyed ubuntu.

---

### Post by Jerad on 2008-02-17
when i double click the sound icon, i get a msg...

No volume control GStreamer plugins and/or devices found.

---

### Post by chips24 on 2008-02-21
still need help here

---

### Post by chips24 on 2008-02-23
anyone?  please

---

### Post by chips24 on 2008-03-04
ive gone 2 weeks without audio now, still need help.

---

### Post by Bargeek on 2008-03-04
Chips, I am having the same exact problem.  Haven't found the answer yet, but if I find something that works for me, I will be sure to let you know.

---

### Post by chips24 on 2008-03-05
do you daulboot?

---

### Post by chips24 on 2008-03-05
heres what i did, it still didnt work



caleb@caleb-laptop:~$ sudo apt-get install alsa
[sudo] password for caleb:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
caleb@caleb-laptop:~$

---

### Post by Redptc on 2008-03-05
Sound seems to trouble a lot of people but there is talk that Hardy Heron is going to reverse this trend. It comes out in another month or so and I hope It does sort many of these sound problems.

I can only refer you to the thread that did help me.......[http://ubuntuforums.org/showthread.php?t=682383&highlight=redptc](http://ubuntuforums.org/showthread.php?t=682383&highlight=redptc)

If you set a card as default you may have to juggle your preferences.

Best of Luck!

---

### Post by Bargeek on 2008-03-05
Chip,

Sorry it took so long to reply, but I was heading to work when I posted.

Got home today, dug around for a couple of hours to no avail.

Just tinkering around, I noticed that I could call up alsamixer in the terminal, but it wasn't listed under my sound applications in the GUI.  So I went to add/remove under my Applications, installed alsa mixer (it wasn't installed, somehow,) and then started playing around with the sliders.  I noticed when I increased the levels on the headphones, my speakers started hissing.

Then I went into System > Preferences > Sound and ran a test.  I nearly had a heart attack, not only did I have sound, but it was unexpectedly LOUD.  I had the headphone levels all the way up.

Anyhow, I am pleased to report that I now have sound.  Don't understand why my speakers are controlled by the headphone slider, but it works, so I am NOT asking any questions.

Hope this works for you!!

---

### Post by chips24 on 2008-03-05
didnt work, however i did install the alsa mixer and restarted my puter, but still no audio.

---

### Post by Bargeek on 2008-03-06
Sorry that didn't help.  I was amazed when it turned out to be something so simple for me.  

Wish I had something else to suggest, but I honestly hope it works out for you!!

---

### Post by chips24 on 2008-03-08
well, i didnt do anything, it just turned on on its own.

---

### Post by Josh C on 2008-03-09
That happened to me awhile back.  I lost audio and then one day while doing a reboot I had system sounds again.  When I logged into Ubuntu I had all my sound back.  For some reason, as of yesterday, I no longer have sound anymore.

josh@josh-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: 30000000-300fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18b0 [size=8]
        I/O ports at 18a4 [size=4]
        I/O ports at 18a8 [size=8]
        I/O ports at 18a0 [size=4]
        I/O ports at 1890 [size=16]
        Memory at d0544400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1363
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at 2000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

I sure hope the next Ubuntu release fixes these issues.  Until then, any suggestions...

---

### Post by chips24 on 2008-03-09
no, im just an amature

---

### Post by skylinedna on 2008-03-10
There was a thread around here im sure it was a sticky. something alond the lines of knowen 7.10 bugs and workarounds. i trying to find it because it fixed this problem for me the last time i had it and i just completed a fresh install and bam it happens again. if anyone can find this thread it might help

---

