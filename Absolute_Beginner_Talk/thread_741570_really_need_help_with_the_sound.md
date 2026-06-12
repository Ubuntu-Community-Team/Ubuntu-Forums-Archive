---
title: "really need help with the sound"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by prtoxicalsoul on 2008-03-31
After trying many methods and having them all fail, I have no choice but ask for some personal help. Like many others my sound does not work, there is a null sign on my volume control. when i press it i get two error messages.

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

No volume control GStreamer plugins and/or devices found.

when i type lspci -v in terminal i get 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

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

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 20
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

im running a toshiba satellite A135-S4487 

and i noe my sound card works because im dual booting and it works on my vista.
also when i installed ubuntu 8.04 sound works on that although the headphone jack didnt work. I went back to version 7 because 8.04 had a wireless issue, and i figuared having wireless was more important.

anyone give me a hand here?

---

### Post by Inxsible on 2008-03-31
Lets start with the basics here. Type in ```
alsamixer
``` in a terminal and max all volume levels. See if that works. You getting a null pointer on the volume control button is weird though.

---

### Post by prtoxicalsoul on 2008-03-31
i got the code

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by Inxsible on 2008-03-31
> **prtoxicalsoul said:**
> i got the code

alsamixer: function snd_ctl_open failed for default: No such deviceOk so its not even recognizing the hardware.  Is this a new machine ?

---

### Post by prtoxicalsoul on 2008-03-31
its not really a new machine i got it december of 2007. what is weird was that ubuntu v8.04 was able to recognize it.

---

### Post by Inxsible on 2008-03-31
> **prtoxicalsoul said:**
> its not really a new machine i got it december of 2007. what is weird was that ubuntu v8.04 was able to recognize it.I just checked my machine and I have the same sound controller as you and mine works. So its probably some small issue.

---

### Post by prtoxicalsoul on 2008-03-31
any idea what the issue is, because i tried everything online and nuthing seems to work. thanks for ur help so far

---

### Post by Inxsible on 2008-03-31
> **prtoxicalsoul said:**
> any idea what the issue is, because i tried everything online and nuthing seems to work. thanks for ur help so far
I am not really sure. I have tagged your thread in the unanswered posts, so someone will definitely try and help you out.

But, if your install is just recent, you can try and re-install the OS. That could potentially fix the problem.

---

### Post by prtoxicalsoul on 2008-03-31
yea i reinstalled it a couple times now, even during the live session the null sign was on my volume control too. thanks for the help anyways!

---

### Post by rkd on 2008-03-31
This sometimes helps get the audio working:
```
sudo apt-get install linux-backports-modules
```
It loads more up-to-date software than in the standard installation.  The place I read about it says you must reboot after installing to get the changes to take effect.

---

### Post by prtoxicalsoul on 2008-03-31
OMG THAT ACTUALLY WORK THANKS ALOT!! to think i wasted 2 hours doing complicated procedures before.

now all i have to figuare out how get the headphone to work @_@ rite now when i plug my headphone no sound comes out, and the speaker keeps going

---

### Post by rkd on 2008-04-01
You're welcome.  I think I've seen a thread a while ago talking about a problem similar to what you describe with your headphones.  I don't remember the details, but I think it was some fairly easy configuration thing.  I'll try to find it for you, but it might take a while to locate it.

---

### Post by prtoxicalsoul on 2008-04-01
ill try looking too, thanks for the help so far

---

### Post by rkd on 2008-04-03
Okay, I found the post I was looking for.  It wasn't actually a post; it was in the Community Documentation.

There may be two separate problems: not turning off the speakers and not sending any sound to the headphones.

For not turning off the speakers, the simplest fix involves turning on the Headphone Jack Sense. One way is:

Go to applications > sound/video > sound recorder > file menu > open volume control. Click the Switches tab. You should see a Headphone Jack Sense option.  Make sure it is checked.

There are other ways to turn on that Headphone Jack Sense, but this one seemed simplest.

The problem about no sound from the headphones might be that the sound is muted.  So go to the volume control or mixer and make sure that if there is a Headphone control, it isn't muted and the level is not at 0.  If there is no Headphone control, make sure the PCM is enabled and not at 0.

If the above doesn't fix the problems, or you can't even find the controls mentioned, try the other approach of adding an option into the alsa configuration. The exact option depends on your hardware.  You put the option into the file /etc/modprobe.d/alsa-base, using whatever editor you like (don't forget sudo or gksu or kdesu, as appropriate).  I have found posts giving the correct line for various models of Toshiba Satellite A135-xxxxx:

```
options snd-hda-intel position_fix=1 model=3stack    (A135-S4527)
options snd-hda-intel probe_mask=8 model=3stack      (A135-S2386)
options snd-hda-intel model=3stack                   (A135-S4467)
```

The last is the closest to your model number, and is the simplest, so it might be a good one to try first.

If none of those take care of all the problems, here is where you can dig into the gory details:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Go down to the heading "Manually Specify Module Parameters. A slightly easier way to find the ALSA documentation than what that page shows is this:

```
sudo find /usr -name ALSA-Config*
```

If the file it finds doesn't have the kernel version in the third part of the path, but is /usr/share/doc..., I imagine that is good enough.  If nothing in it works, we can go back and find the right one.

On my system, the file in /user/share/doc... is gzip compressed, so I copied it to my home directory and used gunzip to expand it.  It might be a good idea to copy the file you find to your home directory, even if it doesn't need to be expanded, so you don't accidentally modify it (and so you can give it a shorter name for easier typing). 

Open the file in your favorite editor, page down to the section "Module snd-hda-intel", look at the options for your sound chip, and decide which ones to try.

Each time you change the option and reboot, check to see whether the Headphone Jack Sense is enabled and check that the necessary channels are not muted or too low level.  There are other tips in the Howto as well.

---

