---
title: "weird sound problem"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by natman on 2007-05-10
Hi i have kubuntu 7.04 and most things are ok, For about 60% of my boot ups the sound works fine, but the rest of the time the there is no sound ( nothing ). This seems to be random, can anyone shed some light on this problem.
I have a conexant venice sound card, laptop details below.
Thanks:

---

### Post by Pragmatist on 2007-05-10
> **natman said:**
> Hi i have kubuntu 7.04 and most things are ok, For about 60% of my boot ups the sound works fine, but the rest of the time the there is no sound ( nothing ). This seems to be random, can anyone shed some light on this problem.
I have a conexant venice sound card, laptop details below.
Thanks:

1. Check your volume and make sure it isn't set to mute.  Also, make sure the volume isn't set really low.

2. Go to the menus and select System-->Preferences-->Sound   What do the settings indicate?   In particular, note the default sound card under the "sound" tab.

3.  Does your motherboard have on-board sound?  If it does, go into your BIOS and disable it, you can always go back and re-enable it later.  This will allow you to troubleshoot one card at a time.  To test the reverse, I would remove the sound card and re-enable the on-board sound.  If you prefer not to physically remove the sound card, I'm sure there are other ways.  This is just what I would do.

Let us know what you discover.

---

### Post by natman on 2007-05-13
I tried what you said but it made no difference, as to the motherborad and different sound cards, thats a little over my head and probably not the cause since the sound works on random boot ups.

also when i was in the sound menu, i clcked "test" and the GUI shut down straigh away, does that mean anything bad?

---

### Post by Pragmatist on 2007-05-13
I didn't notice at first that you have a laptop.  It is not likely that you have multiple sound cards.

After some research it seems other have had similar problems.  You might want to try the suggestions in this thread: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This is general for Intel HD Sound.  If it doesn't work, the next thing is to try and find something specific from Conexant.  Apparently your hardware is somewhat new, and I read that Conexant was working with ALSA to develop something specific.

Personally, I would try the suggestions in the above thread.  It might be even easier for you since your problem is mentioned along with a guess as to it's "flavor"

"Sound works at random after each reboot (possibly flavour 'm2-2' below)"

This will make this categorical approach a little more specific.

Good luck and keep us posted.

---

### Post by natman on 2007-05-13
Hey,
I had a look athe thread and was unable to disable any sound card in the bios ( had a look on the net and most people are complaining that laptop BIOS are simple and dont give any advanced options - i dont have a password for the power on or boot up ).
But i went ahead and tried the new alsa files and did what it told me. First off the sound is improved ( when its there at all ) i now get better sound at lower volumes. But the core issue of no sound at random boots is still there. Im sure like you said that the thread and bios have the answer or wait till the next ubuntu/update.

If you have any ideas on the bios that would be cool, but i fear its a problem i will have for a while. Very annoying when you buy a nice new laptop and it only works fully in windows. Oh well thanks for all your time and very good help. Also the help link on your signature is fantastic- thank you!.

Patrick

---

### Post by Pragmatist on 2007-05-13
EDIT: Sorry, I have edited this a few times.  The major changes were now there is a script rather than individual commands.  And, the filename sound_info was changed to sound_info.sh (to follow attachment rules)

I'm happy to help.  Don't worry about the BIOS for now.  I'd mentioned it on the assumption that you were not using a laptop and might have more than one sound card.  The thread's BIOS suggestion has to do with a different problem than the one your having (i.e. your system is booting, your just not always getting sound).

So, lets get some basic information. I have attached a simple script which will give us the info we need, and save you some typing :).  Save it to your computer using the filename "sound_info.sh" and then do the following inside a terminal:

```
chmod a+x sound_info.sh
```Now run the script twice. First, when your system has sound.  Second, when your system does not have sound.  Here is how you run the script when you have sound 

```
./sound_info.sh sound.txt
```When you don't have sound:

```
./sound_info.sh nosound.txt
```You will now have two files, one called "sound.txt" and one called "nosound.txt".   Attach both files here.

---

### Post by natman on 2007-05-13
Sorry if this is totally stupid, but where did you put the script "sound_info". I cant see any link to it or way to download it.

---

### Post by natman on 2007-05-13
Of course once i posted i know see the attachment - duh!!

---

### Post by natman on 2007-05-14
Okay they are large files so i hate to make two posts. Here is sound.txt  (see attachment below )
[HTML]Linux natman-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux


Mixers:
0: Conexant CX20549 (Venice)


Names of available sound cards:
Intel


snd_hda_intel          24224  4 
snd_hda_codec         262912  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm


           CPU0       CPU1       
  0:      30204          0   IO-APIC-edge      timer
  1:        165          0   IO-APIC-edge      i8042
  8:          0          0   IO-APIC-edge      rtc
  9:       3022          0   IO-APIC-fasteoi   acpi
 12:        133          0   IO-APIC-edge      i8042
 14:       1185          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:          2          0   IO-APIC-fasteoi   uhci_hcd:usb4, ohci1394
 18:          0          0   IO-APIC-fasteoi   sdhci:slot0
 19:       5283          0   IO-APIC-fasteoi   uhci_hcd:usb2, ipw3945
 20:       9099          0   IO-APIC-fasteoi   libata, eth0
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:       2678          0   IO-APIC-fasteoi   HDA Intel
 23:        551          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
NMI:          0          0 
LOC:      30066      30042 
ERR:          0


00:00.0 0600: 8086:27a0 (rev 03)
	Subsystem: 103c:30b2
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 0604: 8086:27a1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 103c:30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 0604: 8086:27d0 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2000000-d3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>

00:1c.2 0604: 8086:27d4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1c.3 0604: 8086:27d6 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: d6000000-d60fffff
	Capabilities: <access denied>

00:1d.0 0c03: 8086:27c8 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1800 [size=32]

00:1d.1 0c03: 8086:27c9 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]

00:1d.2 0c03: 8086:27ca (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1d.3 0c03: 8086:27cb (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]

00:1d.7 0c03: 8086:27cc (rev 02) (prog-if 20 [EHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d6404000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 0604: 8086:2448 (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6100000-d61fffff
	Capabilities: <access denied>

00:1f.0 0601: 8086:27b9 (rev 02)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 0101: 8086:27df (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]

00:1f.2 0101: 8086:27c4 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: 103c:30b2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d6404400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 0c05: 8086:27da (rev 02)
	Subsystem: 103c:30b2
	Flags: medium devsel, IRQ 20
	I/O ports at 18e0 [size=32]

01:00.0 0300: 10de:01d6 (rev a1) (prog-if 00 [VGA])
	Subsystem: 103c:30b2
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=128M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at c8000000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 0280: 8086:4222 (rev 02)
	Subsystem: 103c:135c
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

08:08.0 0200: 8086:1092 (rev 02)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at d6100000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

08:09.0 0c00: 1180:0832 (prog-if 10 [OHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d6101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:09.1 0805: 1180:0822 (rev 19)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at d6101800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.2 0880: 1180:0843 (rev 01)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at d6101c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.3 0880: 1180:0592 (rev 0a)
	Subsystem: 103c:30b2
	Flags: medium devsel, IRQ 11
	Memory at d6102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.4 0880: 1180:0852 (rev 05)
	Subsystem: 103c:30b2
	Flags: medium devsel, IRQ 11
	Memory at d6102400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>



Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Front Left: Playback 28 [65%] [on]
  Front Right: Playback 28 [65%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'LineIn',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Ext Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Limits: 0 - 23
  Mono: 10 [43%]
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Int Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Limits: 0 - 23
  Mono: 23 [100%]
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'IntMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on][/HTML]

---

### Post by natman on 2007-05-14
And here is "nosound.txt"

[HTML]Linux natman-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux


Mixers:
0: Conexant CX20549 (Venice)


Names of available sound cards:
Intel


snd_hda_intel          24224  4 
snd_hda_codec         262912  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm


           CPU0       CPU1       
  0:     154348          0   IO-APIC-edge      timer
  1:        783          0   IO-APIC-edge      i8042
  8:          0          0   IO-APIC-edge      rtc
  9:      13239          0   IO-APIC-fasteoi   acpi
 12:        133          0   IO-APIC-edge      i8042
 14:       6641          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:          2          0   IO-APIC-fasteoi   uhci_hcd:usb4, ohci1394
 18:          0          0   IO-APIC-fasteoi   sdhci:slot0
 19:      25260          0   IO-APIC-fasteoi   uhci_hcd:usb2, ipw3945
 20:      35329          0   IO-APIC-fasteoi   libata, eth0
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:       9344          0   IO-APIC-fasteoi   HDA Intel
 23:      13700          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
NMI:          0          0 
LOC:     154211     154187 
ERR:          0


00:00.0 0600: 8086:27a0 (rev 03)
	Subsystem: 103c:30b2
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 0604: 8086:27a1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 103c:30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 0604: 8086:27d0 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2000000-d3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>

00:1c.2 0604: 8086:27d4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1c.3 0604: 8086:27d6 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: d6000000-d60fffff
	Capabilities: <access denied>

00:1d.0 0c03: 8086:27c8 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1800 [size=32]

00:1d.1 0c03: 8086:27c9 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]

00:1d.2 0c03: 8086:27ca (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1d.3 0c03: 8086:27cb (rev 02) (prog-if 00 [UHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]

00:1d.7 0c03: 8086:27cc (rev 02) (prog-if 20 [EHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d6404000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 0604: 8086:2448 (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6100000-d61fffff
	Capabilities: <access denied>

00:1f.0 0601: 8086:27b9 (rev 02)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 0101: 8086:27df (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]

00:1f.2 0101: 8086:27c4 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: 103c:30b2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d6404400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 0c05: 8086:27da (rev 02)
	Subsystem: 103c:30b2
	Flags: medium devsel, IRQ 20
	I/O ports at 18e0 [size=32]

01:00.0 0300: 10de:01d6 (rev a1) (prog-if 00 [VGA])
	Subsystem: 103c:30b2
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=128M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at c8000000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 0280: 8086:4222 (rev 02)
	Subsystem: 103c:135c
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

08:08.0 0200: 8086:1092 (rev 02)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at d6100000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

08:09.0 0c00: 1180:0832 (prog-if 10 [OHCI])
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d6101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:09.1 0805: 1180:0822 (rev 19)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at d6101800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.2 0880: 1180:0843 (rev 01)
	Subsystem: 103c:30b2
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at d6101c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.3 0880: 1180:0592 (rev 0a)
	Subsystem: 103c:30b2
	Flags: medium devsel, IRQ 11
	Memory at d6102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.4 0880: 1180:0852 (rev 05)
	Subsystem: 103c:30b2
	Flags: medium devsel, IRQ 11
	Memory at d6102400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>



Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Front Left: Playback 27 [63%] [on]
  Front Right: Playback 27 [63%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'LineIn',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Ext Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Limits: 0 - 23
  Mono: 10 [43%]
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Int Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Limits: 0 - 23
  Mono: 23 [100%]
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'IntMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
[/HTML]


There is some more text on the output (see attachment below ). Not sure if this makes a difference, but my system is a 64 bit kubuntu.

---

### Post by Pragmatist on 2007-05-14
So far I haven't noticed anything unusual.  It probably will be solved eventually when a new driver is made.  But, I haven't given up yet, if you haven't.

If you do need to wait, one solution to ensure sound now, would be to get an external sound card.  They aren't too expensive and they plug in directly to USB.    I had one years ago and it was only the size of a pack of cigarettes. Whenever you buy hardware you want to check out to see if the model is known to work.  I would go to the ALSA website to see.  Also, often devices that work with Mac OSX will work with linux.  If your not certain, make sure the computer store has an acceptable return policy.

I will post more about getting your current card to work after I do some more research.

---

### Post by natman on 2007-05-18
Hi again,
Just wanted to give an update on whats going on with my laptop and sound, for the last week sound has worked perfectly. I can only thing of two things that have happened since, i got some updates from adept, and i had a problem with mime not knowing some extenions (no sound as far as i could see ).
Lets hope things have fixed themselves.
Thanks:

---

### Post by natman on 2007-05-30
Hi again,
Just a futher update, i turned on the machine after a week of full windows booting. the sound failed, then i applied my updates and seem to have gotten the latext kernel ( 2 6 20 - think) and first new boot and sound works - lets hope it keeps up:)

Later:

---

### Post by natman on 2007-06-24
Hi again,
I still have my sound problem, but i have just noticed something kinda weird, ( i also have  a problem with firefox and flash, [http://ubuntuforums.org/showthread.php?t=476483](http://ubuntuforums.org/showthread.php?t=476483) )

I am after booting up, no sound , then i went to youtube and played a video, and perfect sound, but amarok, system sounds, noatun, give nothing?

Is there a correlation between the two or am i just grasping at straws?

---

