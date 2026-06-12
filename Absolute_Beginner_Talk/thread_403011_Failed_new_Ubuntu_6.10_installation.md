---
title: "Failed new Ubuntu 6.10 installation"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by movado on 2007-04-06
Hello all:

Need help with a new installation. 

This is my first Linux experience and recently downloaded Ubuntu Desktop Edition 6.10. Created a new CD using ISO Recorder and proceeded to boot from the CD. Got to the initial GUI screen; selected 'Start or install Ubuntu'; the loading process starts, and inmediately stops. The last lines on the screen read as follow:


[17179573.244000] Call Trace:
[17179573.244000] Code: Bad EIP value
[17179573.244000] EIP: [<bfcfdcc7>] 0xbfcfdcc7 SS:ESP 0068:dfa01f3a
[17179573.244000] <0>Kernel panic - not syncing: Attempted to kill init!

I thought it was either a problem with my copy, or a HW issue, therefore changed memory and CD. Didn't change HD, and cannot replace MB.

Downloaded the files from alternative locations. Burned a second copy of Ubuntu using Roxio, and a third copy using Nero.Same error.

My computer configuration is as follow:

CPU: AMD Athlon 
CPU Speed: 950 MHz
Cache Size: 256K
HD: Maxtor IDE 120GB (6Y120L0)
Memory: 512MB (133Mhz)
Chipset VIA KT133/KT133A
BIOS: AMI v.2.02
Under Advance BIOS Setup I have the following option:
PCI Latency Time: 64 (Values can be modifed from 32 to 248 )
AGP Aperture Size: 64MB (Values can be modified from 4 to 256)
Close DIMM/PCI Clock: No (Alternative is Yes) 

I tried going into text mode. Got to boot: prompt, but from there I'm not sure what to do. I remeber there is a ls command to see  directory structure, but apparently there is no such command on this CD. Bottom line, I'm stuck. 

Any suggestions and recommendations are fully appreciated.

 - Movado -

---

### Post by tchoklat on 2007-04-06
[http://ubuntuforums.org/showthread.php?t=172184](http://ubuntuforums.org/showthread.php?t=172184)
 
when booting at the first menu press F6 and then type noapic at prompt and press enter
 
 
tchoklat

---

### Post by tgm4883 on 2007-04-06
How fast are you burning the cd?  Did you check the cd after burning?  Did you check it using the check cd option (something like the 3rd one down when booting)?

---

### Post by movado on 2007-04-06
The CDs burned at about 16X, although my burner can do faster than that. The answer to your third question is yes, but I got the same error as before, 

Previously, I replaced the CD with anohter unit and got similar error.

- Movado -

---

### Post by movado on 2007-04-06
Thanks  for your fast response. Tried using F6 / noapic combination. Same error. I'm suspecting there is something wrong w/ the IDE controller. It is the second embedded controller on the MB. I'll try setting the player as slave on the first controller and see what happens. I'll keep you posted.

- Movado -

---

### Post by X-Cyber on 2007-07-10
I don't now if movado resolved this issue. I'm installing Kubuntu 7.04 in a Gateway PC, very similar to your specs.

I had the same problem, and finally a _***BIOS update***_ resolved the issue.

I tried all the boot parameters, replaced memory modules, tried different CD drives, etc. as mentioned in these forums, but nothing worked in this case.

Note: I tried different Linux distributions, and all of them crashed with the buggy BIOS; only *BSD worked before the update.

---

