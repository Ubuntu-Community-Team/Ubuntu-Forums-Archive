---
title: "no sound 12.04 mac pro"
date: 2012-09-19
forum: Apple Hardware Users
---

### Post by Arterrious on 2012-09-19
I have a mac pro tower (early 2009 i think) and i have a fresh install of ubuntu 12.04 on it but i can get any sound to work. speakers are connected and turned on, alsamixer isn't muted, and i haven't found any solutions on any other threads. can anyone help?

---

### Post by Arterrious on 2012-09-20
the system isn't muted as far as i can tell. the drivers that are installed are the ones that came with the OS; I haven't made any changes. i saw on some other threads that alsamixer has an automute toggle that i have disabled and i made sure that everything was OO instead of MM. some other threads were saying that if i add something like "options something something model=macpro" to the end of a certain file in modprobe.d it would fix the sound but when i restarted the computer i got some "disabling IRQ #17" error and the computer wouldn't boot so i just reinstalled... i'm not sure what to do.

---

### Post by Arterrious on 2012-09-25
anyone got any ideas?

---

### Post by Arterrious on 2012-10-10
output volume is 100% but there is no sound. once again this is a fresh install of ubuntu 12.04.

This is what the computer says my sound card is:

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 66
	Memory at 90520000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

I think my graphics card may be interfering with the sound.

05:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress XT [Radeon HD 5870] (prog-if 00 [VGA controller])
	Subsystem: Apple Inc. Device 00d0
	Flags: bus master, fast devsel, latency 0, IRQ 68
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90400000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at 90420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

05:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cypress HDMI Audio [Radeon HD 5800 Series]
	Subsystem: Apple Inc. Device aa50
	Flags: bus master, fast devsel, latency 0, IRQ 67
	Memory at 90440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

i cant find any information on the internet on how to fix this issue - or at least define the issue.

---

### Post by cbanakis on 2012-10-10
Try the headphone jack on the front.

---

### Post by Arterrious on 2012-10-11
neither of the jacks work. The only thing i would like to get working is the built in sound controller on the motherboard; the graphics card should only handle graphics. :-k

This is what alsamixer says by the way...

[http://ubuntuforums.org/attachment.php?attachmentid=225411&stc=1&d=1349977232](http://ubuntuforums.org/attachment.php?attachmentid=225411&stc=1&d=1349977232)

and just in case it helps, here's my sound settings:

[http://ubuntuforums.org/attachment.php?attachmentid=225412&stc=1&d=1349977487](http://ubuntuforums.org/attachment.php?attachmentid=225412&stc=1&d=1349977487)

---

### Post by Sonblind on 2012-10-24
I have the same problem. I am running a 2009 Mac Pro tower Nehalem 8 core. I have Linux Mint 13, but tried booting Ubuntu 12.4 from disc and I have NO sound on both OS, not even when testing the speakers in sound preferences. I am using the head phone jack. It's not muted...

---

### Post by Arterrious on 2013-02-07
I still haven't found a fix... :confused:

---

### Post by serpico007 on 2013-03-01
I'm in the same boat with my macbook pro. I plug in the headphones and volume is very low. I checked everything and nothing is muted. I can't believe that in 2013 we still can't get things working out of the box.

---

### Post by thebestguy on 2013-03-01
call to the customer care.





follow: [www.twitter.com/updatesbest]("http://www.twitter.com/updatesbest")

like:[www.facebook.com/thebfsu](www.facebook.com/thebfsu) :P

---

### Post by mr_manny on 2013-03-02
I noticed something similar.
Went into the gnome-control-panel and changed the settings under the hardware tab (as well as test).

It's worth a try :)

---

