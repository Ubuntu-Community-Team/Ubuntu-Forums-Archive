---
title: "PowerMac G5 1.6Ghz... ?"
date: 2004-10-27
forum: Apple PPC Users
---

### Post by MachineShedFred on 2004-10-27
Greetings.

So I am trying to get the new "warty" release to boot and install on this here Power Mac G5 1.6Ghz with the latest Open Firmware release (5.1.5f2), and after I tell it to install (options don't seem to matter - I've tried -power4, video=ofonly, expert=ofonly) it dumps me to an Open Firmware screen with a locked up keyboard and does nothing.  Here is the information on the screen:

```

... ok
opening display /pci@0, f0000000/NVDA,parent@10/NVDA,Display-A@0... ok
copying 0F device tree...done
Initializing fake screen:  NVDA,Display-B
Calling quiesce ...
returning 0x01400000 from prom_init

Invalid memory access at    %SRR0:  00000000.01403b88     %SRR1:  10000000.00083030

Apple Powermac 7,2 5.1.5f2 BootROM built on 09/21/04 at 11:58:53
Copyright 1994-2004 Apple Computer, Inc.
All Rights Reserved

Welcome to Open Firmware, the system time and date is 22:46:07  10/27/2004

To continue booting, type 'mac-boot' and press return
To shut down, type 'shut-down' and press return

Release keys to continue!

``` 

At this point, I can hear the CD spin down, and all the fans gradually speed up to filling-rattling volume.

So, as I haven't found this error anywhere on the web, I figure I just must be doing something wrong that is so obvious that I will probably want to hurt myself once one of you points it out.  Any takers?

Other information:  SATA hard disk has one partition, Journalised HFS+ which I was planning on blowing away.  Open Firmware password is enabled, though I can disengage this if someone thinks it is a problem.  I have tried other Linux distros in the past with it disabled and it seems to have the same effect (gentoo crashes out horribly, YDL 3.0 does this same thing with the Open Firmware screen).

Cheers!

---

### Post by dspivey on 2004-11-02
I don't have a resolution for you, but I have the EXACT same problem with my G5.  Ubuntu installs just fine on a G4, though.

---

### Post by TheVexedSoul on 2004-11-09
I'm having the same problem...

---

### Post by jdusablon on 2004-11-10
G5 is not the same type of PPC as G3 and G4. There are some fairly significant architecural differences between G3/G4 and G5, namely, the ability to run 64-bit code. Also the transport bus in a G5 is completely different, PCI-X being one of those differences.

In the same way that there is an AMD64 Ubuntu distro, there also will need to be a G5 distro. Some other linuxes/unices are already doing this, try them.

---

### Post by sumanjay on 2004-11-10
Agree with jdusablon - Ubuntu doesn't appear to have a G5 version going yet. You might wanna give Yellow Dog 4.0 a try; that and Gentoo are the only distros I know that have G5 support. Gentoo is a bit of a pain to install, even if you go the easy way and do a Stage 3 one. Yellow Dog should be releasing ISOs of v4.0 for free download in the near future.

---

### Post by TheVexedSoul on 2004-11-10
Really? I've seen on many news sites that Ubuntu became G5-compatible at least a month ago. Either way, I tried installing Gentoo and the same problem occurred. I guess I'll just wait until the YDL 4.0 ISOs are released and see what happens.

---

### Post by pdkline on 2004-12-02
Same problem when i dont do 
'install-power4'

note there is no space, it took me a bit to realize it, after it failed a few times, i hit tab to see what other kernels, then i realize there is no space.

I can get it to boot up then (NVidia card) to start the install, then the keyboard goes bad and funky.. i.e. looks like the  keyboard gets stuck.

Paul

---

### Post by Viro on 2004-12-05
[QUOTE=jdusablon]G5 is not the same type of PPC as G3 and G4. There are some fairly significant architecural differences between G3/G4 and G5, namely, the ability to run 64-bit code. Also the transport bus in a G5 is completely different, PCI-X being one of those differences.

In the same way that there is an AMD64 Ubuntu distro, there also will need to be a G5 distro. Some other linuxes/unices are already doing this, try them.[/QUOTE]
 The Athlon64/Opteron is compatible with x86. These can run standard 32 bit Linux distros just fine. You'll need an AMD64 distro if you want to take advantage of the additional features that the new instruction set brings.

The same goes for the G5. It works with PPC code, but you'll be better served with a PPC64 distro since it makes full use of the G5 chip's abilities.

---

### Post by pdkline on 2004-12-06
I really think they need to stop saying G5 is supported, I have a Dual 2.0, 1 Single 1.8, and a Single 1.6 G5 at work.  Ubuntu does NOT run on either of machines.  However, the G4 machines have no problem at all. 

I tested all machines, even took out memory on all of them.  Frankly, I am rather disappointed.  I have went to IRC to talk to the people who compile, and they go "it works on my machine"..  great, but it doesnt work on machines that we ordered directly from apple. :P

maybe I am a little bitter, but they should remove they support the G5 Because obviously its NOT working.

---

### Post by spence on 2004-12-06
YDL 4.0 is available for free download already but this also isn't a 64 bit distribution.  From what you guys are saying it may be marginally better than Ubuntu on a G5 (although I know that sound doesn't work, at least I think it boots.)  The 64 bit OS is Y-HPC which is currently selling for $200.  I would guess that it will never be available for free download as I think that TSS is hoping it will be their cash cow.

---

