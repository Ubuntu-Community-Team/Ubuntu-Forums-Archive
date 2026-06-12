---
title: "Sound working only a few ms on PowerBook G4 1GHz"
date: 2007-10-22
forum: Apple PPC Users
---

### Post by chombier on 2007-10-22
Hello !

I've just updated to Gutsy, and can't use audio on my Titanium PowerBook 1GHz.

With the default settings (ie esd off), I can hear the terminal beep, but can't play any audio file: I can hear the very begining of the sound, but it stops after a less than half a second.
So the sound driver is here and loaded since I can hear the begining.

Using gdb over the command aplay for a wav file (/usr/share/sounds/startup3.wav for instance) shows that the sound player is stuck in poll() called from snd_pcm_wait_nocheck().

> (gdb) set args /usr/share/sounds/startup3.wav
(gdb) run
Starting program: /usr/bin/aplay /usr/share/sounds/startup3.wav
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 805443408 (LWP 5766)]
(no debugging symbols found)
Lecture en cours WAVE '/usr/share/sounds/startup3.wav' : Signed 16 bit Little Endian, Taux 44100 Hz, Stéréo

Program received signal SIGINT, Interrupt.
[Switching to Thread 805443408 (LWP 5766)]
0x0fd1ce70 in poll () from /lib/libc.so.6
(gdb) bt
#0  0x0fd1ce70 in poll () from /lib/libc.so.6
#1  0x0ff48500 in snd_pcm_wait_nocheck () from /usr/lib/libasound.so.2
#2  0x0ff48784 in snd_pcm_wait () from /usr/lib/libasound.so.2
#3  0x0ff4a7cc in snd_pcm_write_areas () from /usr/lib/libasound.so.2
#4  0x0ff5830c in ?? () from /usr/lib/libasound.so.2
#5  0x0ff41bf0 in snd_pcm_writei () from /usr/lib/libasound.so.2
#6  0x10005878 in ?? ()
#7  0x1000611c in ?? ()
#8  0x10007750 in ?? ()
#9  0x10009e50 in ?? ()
#10 0x0fc65380 in ?? () from /lib/libc.so.6
#11 0x0fc655c4 in __libc_start_main () from /lib/libc.so.6
#12 0x00000000 in ?? ()


Am I the only one to have this problem ?


Now for the odd part: lspci doesn't gives any trace of a Sound device:
> $ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev ff)
And worse, a verbose lspci gives a truncated/corrupted (!?) list:
> $ lspci -v
[...]
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW323 (prog-if 10 [OHCI])
        Subsystem: Agere Systems FW323
        Flags: bus master, medium devsel, latency 16, IRQ 40
        Memory at f5000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev ff) (prog-if ff)
        !!! Unknown header type 7f

I'm not sure if this is related, but lspci was one of the output to provide to debug sound troubles...

---

### Post by frog_pilot on 2007-10-22
May be, this discussion can help you [Feisty and Ti PowerBook G4]("http://ubuntuforums.org/showthread.php?t=412151"). AFAIK the audio device isn't connected via pci. It is connected via i2s-bus.

---

### Post by chombier on 2007-10-22
> **frog_pilot said:**
> May be, this discussion can help you [Feisty and Ti PowerBook G4]("http://ubuntuforums.org/showthread.php?t=412151"). AFAIK the audio device isn't connected via pci. It is connected via i2s-bus.
Thanks for your reply. According to this discussion, there may be an incompatibility with the dmasound module, but the new kernel 2.6.22-14 doesn't seem to have such a module, i.e. make menuconfig gives no "PowerMac DMA sound support" option to disable. Maybe I should open a new bug...

---

### Post by ssam on 2007-10-22
i say it is probably the same bug. have a read of [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/87652)

---

### Post by chombier on 2007-10-23
> **ssam said:**
> i say it is probably the same bug. have a read of [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/87652)

This sounds like a bug in the kernel, or a hardware problem (it wouldn't be the first time some buggy hardware needs workarounds).
I added some traces in the pmac sound driver, and discovered that the problems occurs randomly. The DMA transfer stops after a random number of interrputs, with a DEAD status flag instead of the ACTIVE one with no apparent reason.

In the discussion above, someone mentions:
kernel.org 2.6.20.1: Same fault
kernel.org 2.6.19.5: Sound works as expected (as it did in Edgy)

So I installed an older kernel. The latest pre-2.6.20 I could find in ubuntu archive is [url=
http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-11-powerpc_2.6.17.1-11.38_powerpc.deb]2.6.17-11[/url].
Reboot with this kernel ... and the bug is already present, although it is much more difficult to reproduce. I could play several MP3s but it locked with the same symptoms when I tried to play a sample from the Sound Preferences panel. :confused:

---

