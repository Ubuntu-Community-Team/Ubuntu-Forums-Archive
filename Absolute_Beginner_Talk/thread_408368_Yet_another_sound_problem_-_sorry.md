---
title: "Yet another sound problem - sorry"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Urbanmoth on 2007-04-13
Hi Everyone,

I have a sound problem but I know how many posts there have been on this subject so I am sorry to add yet another one but I have tried all the help-yourself I can find.:icon_frown:

I am running on Edgy and everything is working fine, except for sound. 
I can get sound fine when I view a mpg file in the Totum Movie player but I have got no system sounds and (for example) no sound on YouTube. I have run through the guide here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) even to the extent of compiling the ALSA drivers :shock: 

Any help would be appreciated
Some details:
entering aplay -l gives:
[FONT="System"]**** List of PLAYBACK Hardware Devices ****[/FONT]
but nothing else
My motherboard is an A7N8X Deluxe which uses the NVidia NForce2 drivers

entering lspci -v shows that the system knows the on-board sound is there:

[FONT="System"]00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at ce000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8095
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at ce080000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>[/FONT]

I have no idea how to proceed from here. Any help much appreciated.

Thanks in advance,

UM

---

### Post by compiledkernel on 2007-04-13
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

This is a farily comprehensive guide to curing sound solutions. 

Additionally 

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by Urbanmoth on 2007-04-13
Thanks for the reply but...

> **compiledkernel said:**
> [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

This is a farily comprehensive guide to curing sound solutions.

This is the same info as the post I have already tried and it does not help

> **compiledkernel said:**
> Additionally 

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

Nothing here seems to help - most of this assumes the sound is basically working - which it is not on my system.

Any other suggestions ???

---

### Post by flummoxed on 2007-05-05
I installed ubuntu feisty on my friend's machine which is using an A7N8X-E deluxe and he has no sound coming out of his nforce 2 onboard sound either. It's pretty much the same situation as you have, but no one seems to know what the problem is.

---

