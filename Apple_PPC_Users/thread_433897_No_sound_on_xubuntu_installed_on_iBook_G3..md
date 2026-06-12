---
title: "No sound on xubuntu installed on iBook G3."
date: 2007-05-05
forum: Apple PPC Users
---

### Post by prince_alfie on 2007-05-05
I have Xubuntu 6.06 (or 6.10) installed on my 500mhz dual-USB iBook G3. I only get the startup chime but I can't seem to get any sound (or volume control) working on the iBook. Is there any fix for this problem?

I tried to encode a CD using sound juicer but I get no sound during playback.

---

### Post by stmiller on 2007-05-05
Post your output of
lsmod

------------
I think this iBook model uses the snd-powermac module. If that module is not loaded/not listed with the output of lsmod,

try adding these to /etc/modules

snd-powermac
snd-seq

then reboot. Should work.

--------

OR sometimes you just have to do
alsamixer
in a terminal and hit 'M' to unmute the master output, and it will work.

-------

---

### Post by anders_gud on 2007-05-05
> **prince_alfie said:**
> I have Xubuntu 6.06 (or 6.10) installed on my 500mhz dual-USB iBook G3. I only get the startup chime but I can't seem to get any sound (or volume control) working on the iBook.

Please post the output from:

```
cat /proc/cpuinfo 

```

and```
cat /proc/asound/cards

```

Some audio cards has problems with recent kernels...
See[ this]("http://ubuntuforums.org/showthread.php?t=412151") thread.

---

### Post by prince_alfie on 2007-05-06
I just typed in lsmod and I see a 1 beside snd-powermac which is listed within the output. Any other thoughts of what the 1 stands for?


> **stmiller said:**
> Post your output of
lsmod

------------
I think this iBook model uses the snd-powermac module. If that module is not loaded/not listed with the output of lsmod,

try adding these to /etc/modules

snd-powermac
snd-seq

then reboot. Should work.

--------

OR sometimes you just have to do
alsamixer
in a terminal and hit 'M' to unmute the master output, and it will work.

-------

---

### Post by prince_alfie on 2007-05-06
> **anders_gud said:**
> Please post the output from:

```
cat /proc/cpuinfo 

```

and```
cat /proc/asound/cards

```

Some audio cards has problems with recent kernels...
See[ this]("http://ubuntuforums.org/showthread.php?t=412151") thread.

processor       : 0
cpu             : 750CXe
temperature     : 1-3 C (uncalibrated)
clock           : 400.000000MHz
revision        : 34.21 (pvr 0008 2215)
bogomips        : 26.52
timebase        : 16640000
machine         : PowerBook4,1
motherboard     : PowerBook4,1 PowerBook2,2 MacRISC2 MacRISC Power Macintosh
detected as     : 67 (iBook FireWire)
pmac flags      : 0000001f
L2 cache        : 256K unified
pmac-generation : NewWorld

is the first output

and

0 [Tumbler        ]: PMac Tumbler - PowerMac Tumbler
                     PowerMac Tumbler (Dev 16) Sub-frame 0

for the second command.

Any thoughts how should I proceed?

---

### Post by prince_alfie on 2007-05-06
Thanks, I just tried the alsamixer unmuting and it worked! Voila... C'est la Linux... thanks guys :D

---

