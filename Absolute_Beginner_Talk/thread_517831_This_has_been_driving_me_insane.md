---
title: "This has been driving me insane"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by eamonn on 2007-08-05
Hi,

I've been running Ubuntu on my Gateway laptop since Horay Hedgehog and I have never been able to get my sound working. I've followed all the Ubuntu Guides since Hedgehog and nothing, nothing, has worked. I'm sure there's something I'm doing wrong but I don't know enough about linux to know what that might be. I know there are a lot of sound post but could somebody PLEASE help me get sound working on my laptop?

---

### Post by nitro_n2o on 2007-08-05
what is your sound card type?
what happens when your run speaker-test
and did you try alsamixer 
can you find your sound card if you lspci

---

### Post by eamonn on 2007-08-05
what is your sound card type?
what happens when your run speaker-test
and did you try alsamixer
can you find your sound card if you lspci


I don't know what my sound card type is and I don't know how to find out what it is. When I go into the sound preferences menu though two things that show up are "Intel 82801DB-ICH4" and "Intel 82801DB-ICH4-IEC958" I don't know if that has anything to do with my soundcard though.

I have my alsamixer set up and it looks like it's set up in a way so that I would have sound. But, I still don't have sound on my laptop..

The only thing that happens when I run a speaker test is I get more silence.

I don't know what "lspci" is.


Thank you for helping me through this though.

---

### Post by eamonn on 2007-08-05
Okay, I went through "DebuggingSoundProblems" on the Wiki and found out how to do that "lpsci" thing and this is what I got:

> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Rioworks Unknown device 203a
        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 3
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff
        Prefetchable memory behind bridge: 30000000-33ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 34000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Rioworks Unknown device 2030
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 36000000-37fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0203000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 32000000-33fff000 (prefetchable)
        Memory window 1: 38000000-39fff000
        I/O window 0: 00003c00-00003cff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e0201000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Rioworks Unknown device 202d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 3000 [size=256]
        Memory at e0201800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2701
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>



---

### Post by ugm6hr on 2007-08-05
Well at least it recognises your sound card:
> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
Subsystem: Rioworks Unknown device 203a
Flags: bus master, medium devsel, latency 0, IRQ 10
I/O ports at 1c00 [size=256]
I/O ports at 18c0 [size=64]
Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
Memory at e0100800 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

Now to get it to work:
```
alsamixer
```
Post a screenshot of what happens with this.
```
amixer
```
Post the output of this.

In simple terms - most laptop sound works if you unmute all alsamixer channels and maximise al volumes.  Don't believe the descriptions - my headphone socket is "Front" speaker (*not* Headphone!) and the main speakers are "Surround".

You can use the arrow keys in alsamixer to move around and maximise, and the "M" key to mute/unmute channels.

---

### Post by eamonn on 2007-08-05
Here's the screenshot:

[IMG]http://i19.photobucket.com/albums/b164/krebshack/Screenshot.png[/IMG]

And here's the output from "amixer" :
> amixer: Mixer attach default error: No such device

---

### Post by ugm6hr on 2007-08-05
> **eamonn said:**
> Here's the screenshot:

And here's the output from "amixer" :

Hmm.... I don't think I'm going to be able to help here.  amixer has no output, but alsamixer clearly picks something up.

I actually meant for you to post a Terminal picture for:
```
alsamixer
```
But I'm not sure that will help anyway.  But it might give someone else an idea to help you.

---

### Post by eamonn on 2007-08-05
I don't see much need for a screenshot... all it says is:

> alsamixer: function snd_ctl_open failed for default: No such device


---

### Post by ugm6hr on 2007-08-05
> **eamonn said:**
> I don't see much need for a screenshot... all it says is:

How unusual - Gnome alsamixer works, but the CLI alsamixer doesn't.

I have no idea why that might be.  I know there are other sound drivers (OSS), but if you were using that, then I don't think the Gnome alsamixer should work either.

Hopefully someone else will be able to shed light on this issue for you.

---

### Post by eamonn on 2007-08-05
> Gnome alsamixer works, but the CLI alsamixer doesn't.

Does anyone know how this might've happened and how I might fix it?

---

### Post by Nussbaum on 2007-08-05
My guess is you have to do

```

sudo modprobe snd-intel8x0

```

Not 100% sure but I think thats the module for your soundcard. If it gives a succes message it means it has detected it.


If it has you should add

```

snd-intel8x0

```

to your '/etc/modules' file

---

### Post by SpoonBender on 2007-08-11
I have a similar issue. I have an old gateway laptop and Fiesty has been working for a month and now all of a sudden the right speaker won't work.
I tried a pair of headphones and the right earbud is not working either. I don't know if this is my soundcard or software.
Any help would be great!:confused:

---

### Post by SpoonBender on 2007-08-13
Never Mind. I tried Vlc and it works and now XMMS is back to normal too. Odd.

---

