---
title: "How to turn off my laptop speakers when i plug in my headphone jack....."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by garamas on 2007-10-10
ive tried these two things already to no avail......

[http://ubuntuforums.org/showthread.php?t=485605](http://ubuntuforums.org/showthread.php?t=485605)

 [http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/](http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/)

in the terminal when i type in alsamixer i get no option to pull up headphone....

when i go to the terminal and type in “gnome-volume-control” it also does not have a option to chose the "headphonejack sense" although i have the line jack sense....

this is very frustrating because i already blew my laptop speakers not know that they were on full blast.

i would appreciate any help

---

### Post by gubemton on 2007-10-14
Simple, it's a few steps.

$ amixer controls

Get the NUMID of Master Mono, and then type:

$ amixer cset numid=[..] '0%'

That's it.

---

### Post by avdzm on 2007-11-06
hey,

I have the same problem, but i don't have Master Mono,
Here is my list when i type amixer controls,

numid=3,iface=MIXER,name='Headphone Playback Switch'
numid=13,iface=MIXER,name='PCM Playback Volume'
numid=7,iface=MIXER,name='Front Mic Playback Switch'
numid=6,iface=MIXER,name='Front Mic Playback Volume'
numid=2,iface=MIXER,name='Front Playback Switch'
numid=1,iface=MIXER,name='Front Playback Volume'
numid=5,iface=MIXER,name='Mic Playback Switch'
numid=4,iface=MIXER,name='Mic Playback Volume'
numid=9,iface=MIXER,name='Capture Switch'
numid=8,iface=MIXER,name='Capture Volume'
numid=12,iface=MIXER,name='Caller ID Switch'
numid=14,iface=MIXER,name='Digital Capture Volume'
numid=10,iface=MIXER,name='Input Source'
numid=11,iface=MIXER,name='Off-hook Switch'

any ideas?

---

### Post by rafar on 2007-11-07
I'd like to know this as well. Thanks in advance.

```
amixer controls
numid=3,iface=MIXER,name='Headphone Playback Switch'
numid=21,iface=MIXER,name='PCM Playback Volume'
numid=7,iface=MIXER,name='Front Mic Boost'
numid=9,iface=MIXER,name='Front Mic Playback Switch'
numid=8,iface=MIXER,name='Front Mic Playback Volume'
numid=2,iface=MIXER,name='Front Playback Switch'
numid=1,iface=MIXER,name='Front Playback Volume'
numid=11,iface=MIXER,name='Line Playback Switch'
numid=10,iface=MIXER,name='Line Playback Volume'
numid=13,iface=MIXER,name='CD Playback Switch'
numid=12,iface=MIXER,name='CD Playback Volume'
numid=4,iface=MIXER,name='Mic Boost'
numid=6,iface=MIXER,name='Mic Playback Switch'
numid=5,iface=MIXER,name='Mic Playback Volume'
numid=15,iface=MIXER,name='PC Speaker Playback Switch'
numid=14,iface=MIXER,name='PC Speaker Playback Volume'
numid=17,iface=MIXER,name='Capture Switch'
numid=16,iface=MIXER,name='Capture Volume'
numid=20,iface=MIXER,name='Caller ID Switch'
numid=22,iface=MIXER,name='Digital Capture Volume'
numid=18,iface=MIXER,name='Input Source'
numid=19,iface=MIXER,name='Off-hook Switch'

```

---

### Post by TorbX on 2007-11-10
I have the same problem
> numid=3,iface=MIXER,name='Headphone Playback Switch'
numid=17,iface=MIXER,name='PCM Playback Volume'
numid=11,iface=MIXER,name='Front Mic Boost'
numid=7,iface=MIXER,name='Front Mic Playback Switch'
numid=6,iface=MIXER,name='Front Mic Playback Volume'
numid=2,iface=MIXER,name='Front Playback Switch'
numid=1,iface=MIXER,name='Front Playback Volume'
numid=10,iface=MIXER,name='Mic Boost'
numid=5,iface=MIXER,name='Mic Playback Switch'
numid=4,iface=MIXER,name='Mic Playback Volume'
numid=9,iface=MIXER,name='Aux Playback Switch'
numid=8,iface=MIXER,name='Aux Playback Volume'
numid=13,iface=MIXER,name='Capture Switch'
numid=12,iface=MIXER,name='Capture Volume'
numid=16,iface=MIXER,name='Caller ID Switch'
numid=18,iface=MIXER,name='Digital Capture Volume'
numid=14,iface=MIXER,name='Input Source'
numid=15,iface=MIXER,name='Off-hook Switch'


---

### Post by ghonz on 2007-11-11
I also have the same issue:

numid=3,iface=MIXER,name='Headphone Playback Switch'
numid=21,iface=MIXER,name='PCM Playback Volume'
numid=7,iface=MIXER,name='Front Mic Boost'
numid=9,iface=MIXER,name='Front Mic Playback Switch'
numid=8,iface=MIXER,name='Front Mic Playback Volume'
numid=2,iface=MIXER,name='Front Playback Switch'
numid=1,iface=MIXER,name='Front Playback Volume'
numid=11,iface=MIXER,name='Line Playback Switch'
numid=10,iface=MIXER,name='Line Playback Volume'
numid=13,iface=MIXER,name='CD Playback Switch'
numid=12,iface=MIXER,name='CD Playback Volume'
numid=4,iface=MIXER,name='Mic Boost'
numid=6,iface=MIXER,name='Mic Playback Switch'
numid=5,iface=MIXER,name='Mic Playback Volume'
numid=15,iface=MIXER,name='PC Speaker Playback Switch'
numid=14,iface=MIXER,name='PC Speaker Playback Volume'
numid=17,iface=MIXER,name='Capture Switch'
numid=16,iface=MIXER,name='Capture Volume'
numid=20,iface=MIXER,name='Caller ID Switch'
numid=22,iface=MIXER,name='Digital Capture Volume'
numid=18,iface=MIXER,name='Input Source'
numid=19,iface=MIXER,name='Off-hook Switch'

---

