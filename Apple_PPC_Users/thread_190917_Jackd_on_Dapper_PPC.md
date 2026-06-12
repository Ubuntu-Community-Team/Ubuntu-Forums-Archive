---
title: "Jackd on Dapper PPC"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by Ububurns on 2006-06-06
Is anyone able to run jackd on ppc?

I have tried for **hours** to get it to work.

The soundcard is compatible with the jack and alsa, as I am able to run jackd successfully (on a PC) with the same sound card (a SoundBlaster Live!)

The output of my command to run jackd ($ jackd -d alsa -d hw:0) is the following:
[SIZE="1"][I]
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa[/I]
[/SIZE]
Any help would be greatly appreciated.

---

### Post by discosammy on 2006-08-08
ububurns,

i see your posts about the sblive/alsa... 

i've been looking for the same information, with as much luck as you appear to have.

i think most people doing creative work just spend the $$$ on mac. they don't even look pc way and linux isn't even on the radar screen.

point?

from what i've gathered/learned, some driver-kernel tweaks will be needed. but in theory it should be possible if we start at the source and build ourselves.

i was doing some research before buying the sblive card, but i'm going to rattle the cages of friends this week.

email me if you want me to holler if i find success.

---

### Post by stmiller on 2006-08-10
Jackd works for me, finally. On my iBook G4 this works:

```
jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -s -S
```

```
stmiller@mahler:~$ uname -a
Linux mahler 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux
stmiller@mahler:~$ cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 533.333000MHz
revision        : 0.1 (pvr 8003 0101)
bogomips        : 36.73
timebase        : 18432000
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld

```

```
stmiller@mahler:~$ jackd --version
jackd version 0.100.0 tmpdir /dev/shm protocol 15
```


Jackd also works on my powermac G5 which is now running ubuntu. Let me know if there's anything I can do here that might help.

---

