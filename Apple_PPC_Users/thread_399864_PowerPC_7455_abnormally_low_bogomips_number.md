---
title: "PowerPC 7455 abnormally low bogomips number"
date: 2007-04-02
forum: Apple PPC Users
---

### Post by miniteg on 2007-04-02
****Note to admin: this thread has a duplicate in the absolute beginner's forum, that should be deleted****

Hello,

I installed Ubuntu server (Edgy) on a PowerMac G4 quicksilver, 1GHz / 768MB RAM / Bus 133MHz.

At first I had trouble to get it to start if no screen was connected: things would just die very early on (couldn't even see anything in the logs). After tweaking the list of startup daemons, I got it to work. Point being, maybe I touched something sensitive here, but I'm not sure what.

I then installed a few other things like Gnome, PHP5, MySQL, and Coppermine. The machine is connected to the LAN but has no screen/mouse/keyboard.

Anyway, now it works okay, however I noticed that it takes a very long time to import pictures (when using batch process), much more than needed: about 30 seconds to create a thumbnail and a 800*600 image from a 3.5MB master (about 2300x3500 pixels) using Image Magik ("convert -antialias ..."). I'm sure it can do better! It's a 1GHz G4! Ethernet transfer is very fast, and so is hard drive transfer, but the CPU seems to lag...

And then I noticed that the bogomips number is abnormally low:
[FONT="Courier New"]
miniteg@ubuntu:/proc$ more cpuinfo
processor : 0
cpu : 7455, altivec supported
clock : 999.999997MHz
revision : 0.3 (pvr 8001 0303)
bogomips : 66.56
timebase : 33304558
platform : PowerMac
machine : PowerMac3,6
motherboard : PowerMac3,6 MacRISC3 Power Macintosh
detected as : 129 (PowerMac G4 Windtunnel)
pmac flags : 00000010
L2 cache : 256K unified
pmac-generation : NewWorld[/FONT]

I'm pretty sure that even if the bogomips are bogus (I know how this works), it should still return a bigger number.

So I recompiled a vanilla kernel just for the sake of it, but am getting the exact same performance (note: recompiled with the altivec flag on, to be sure).

So here is the question: how can I make sure that I'm *really* using the most out of this computer?

Thanks,

Teg-

---

### Post by bogoliubov on 2007-04-03
> **miniteg said:**
> 
So here is the question: how can I make sure that I'm *really* using the most out of this computer?


Perhaps you can find a small program that doesn't use any GUI stuff and that use a lot of CPU. So some program that calculates something. Then you can time this program (using the 'time' command) in both OS X and Ubuntu..., if things are OK you should get similar numbers...

There might be an easier way, but none that I know of unfortunately.

Have you checked that the rest of the info about CPU, cache etc is correct?

---

### Post by bogoliubov on 2007-04-03
Hmm, now I saw that it's the same for me on my iBook G4 1.2 GHz:

processor       : 0
cpu             : 7447A, altivec supported
clock           : 599.999000MHz
revision        : 0.2 (pvr 8003 0102)
bogomips        : 36.73
timebase        : 18432000
platform        : PowerMac
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh 
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld

So, this must be some error, but it shouldn't have anything to do with the real speed of your CPU.
Perhaps it's a new definition of Bogomips? :)

---

### Post by ssam on 2007-04-03
this thread explains what is going on

[http://thread.gmane.org/gmane.linux.debian.ports.powerpc/35146/focus=35147](http://thread.gmane.org/gmane.linux.debian.ports.powerpc/35146/focus=35147)

> 2.6.16 doesn't use the some kind of do-nothing loop anymore to set the
bogomips value, but some internal cpu counter or something such. I don't know
the details.

As such, the bogomips value changed radically, and what you see is normal.
bogomips values are bogus anyway, so this change should not have any other
major effect.

> Now on PPC they are related to
the processor timebase frequency, which on G3 and G4 processor
is the bus frequency divided by 4.

---

### Post by miniteg on 2007-04-03
Hello,

Thanks for the replies. Now the bogomip value makes sense.

Plus:
36.73 / 599.999 = 0.0612

and

66.56 / 1000= 0.0665

Good correlation!

Teg-

---

### Post by miniteg on 2007-04-03
Hello,

As suggested by Bogoliubov, I ran a small test program to check the speed of my computer.

Here it is:

Get hold of this zipped tarball somehow (click on the link):

[http://myownlittleworld.com/miscellaneous/computers/files/pi_css5/pi_css5_src.tgz](http://myownlittleworld.com/miscellaneous/computers/files/pi_css5/pi_css5_src.tgz)

Compile and run the thing (type the orange stuff):

[FONT="Courier New"]**miniteg@ubuntu:~/goof_off_hard$ [COLOR="Sienna"]ls[/COLOR]**
pi_css5_src.tgz
**miniteg@ubuntu:~/goof_off_hard$ [COLOR="Sienna"]gzip -d pi_css5_src.tgz [/COLOR]**
**miniteg@ubuntu:~/goof_off_hard$ [COLOR="Sienna"]ls[/COLOR]**
pi_css5_src.tar
**miniteg@ubuntu:~/goof_off_hard$ [COLOR="Sienna"]tar -xvf pi_css5_src.tar[/COLOR]** 
pi_css5_src/
pi_css5_src/fftsg_h.c
pi_css5_src/install.txt
pi_css5_src/Makefile
pi_css5_src/pi_fftcs.c
pi_css5_src/readme.txt
**miniteg@ubuntu:~/goof_off_hard$ [COLOR="Sienna"]ls[/COLOR]**
pi_css5_src  pi_css5_src.tar
[B]miniteg@ubuntu:~/goof_off_hard$ [COLOR="Sienna"]cd pi_css5_src/[/COLOR]
miniteg@ubuntu:~/goof_off_hard/pi_css5_src$ [COLOR="Sienna"]ls[/COLOR][/B]
fftsg_h.c  install.txt  Makefile  pi_fftcs.c  readme.txt[/FONT]

The gcc version I'm using:

[FONT="Courier New"]**miniteg@ubuntu:~/goof_off_hard/pi_css5_src$ [COLOR="Sienna"]gcc -v[/COLOR]**
Using built-in specs.
Target: powerpc-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --disable-softfloat --enable-targets=powerpc-linux,powerpc64-linux --with-cpu=default32 --with-long-double-128 --enable-checking=release powerpc-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
**miniteg@ubuntu:~/goof_off_hard/pi_css5_src$ [COLOR="Sienna"]gcc -O pi_fftcs.c fftsg_h.c -lm -o pi[/COLOR]**
**miniteg@ubuntu:~/goof_off_hard/pi_css5_src$ [COLOR="Sienna"]ls[/COLOR]**
fftsg_h.c  install.txt  Makefile  pi  pi_fftcs.c  readme.txt
**miniteg@ubuntu:~/goof_off_hard/pi_css5_src$ [COLOR="Sienna"]./pi[/COLOR]**
Calculation of PI using FFT and AGM, ver. LG1.1.2-MP1.5.2a.memsave

Usage: ./pi digits

Number of digits of pi to calculate?
**[COLOR="Sienna"]1000000[/COLOR]**
initializing...
nfft= 262144
radix= 10000
error_margin= 0.00579167
calculating 1048576 digits of PI...
AGM iteration
precision= 48: 1.67 sec
precision= 80: 1.66 sec
precision= 176: 1.66 sec
precision= 352: 1.66 sec
precision= 688: 1.66 sec
precision= 1392: 1.66 sec
precision= 2784: 1.65 sec
precision= 5584: 1.66 sec
precision= 11168: 1.66 sec
precision= 22336: 1.66 sec
precision= 44688: 1.66 sec
precision= 89408: 1.66 sec
precision= 178816: 1.66 sec
precision= 357648: 1.66 sec
precision= 715312: 1.65 sec
precision= 1430640: 1.66 sec
writing pi1048576.txt...
[COLOR="DarkGreen"]**31.13 sec. **[/COLOR](real time)
Hit RETURN to exit.
miniteg@ubuntu:~/goof_off_hard/pi_css5_src$ [COLOR="Sienna"]**ls**[/COLOR]
fftsg_h.c  install.txt  Makefile  pi  [COLOR="DarkGreen"]pi1048576.txt[/COLOR]  pi_fftcs.c  readme.txt
**miniteg@ubuntu:~/goof_off_hard/pi_css5_src$** [/FONT]

That's 31.13 seconds then. As a bonus, I got one million digits of pi in the pi1048576.txt file. My Mac Pro ran it in 3.61 seconds with a single core (this program appears to be single threaded).

Maybe someone could post his/her results here so I can get a comparison point... Awwww, come on! You know you want to try it!

Teg-

--------------------------------------------
:guitar: << let's say that's a bass

---

### Post by ssam on 2007-04-04
```
Number of digits of pi to calculate?
1000000        
initializing...
nfft= 262144
radix= 10000
error_margin= 0.00579167
calculating 1048576 digits of PI...
AGM iteration
precision= 48: 1.76 sec
precision= 80: 1.77 sec
precision= 176: 1.76 sec
precision= 352: 1.77 sec
precision= 688: 1.78 sec
precision= 1392: 1.76 sec
precision= 2784: 1.77 sec
precision= 5584: 1.76 sec
precision= 11168: 1.76 sec
precision= 22336: 1.78 sec
precision= 44688: 1.76 sec
precision= 89408: 1.76 sec
precision= 178816: 1.76 sec
precision= 357648: 1.76 sec
precision= 715312: 1.78 sec
precision= 1430640: 1.76 sec
writing pi1048576.txt...
33.67 sec. (real time)
```

on 1ghz G4 powerbook 99.79-bogomips

---

### Post by APU on 2007-04-04
For comparison I have tested it on a PowerBook 12" with a 1.5 GHz G4 under MacOS X 10.4.9 (cant get to my Linux ppc Mac mini until later today but will try this too altough it currently runs Debian testing)

When following the instructions above (they work just the same under OS X) I get 1.22 secs per cycle. If i optimize the binary by using the compiler flag -O2 i get 1.18 secs per cycle (-O3 doesn´t seem to make any difference here).

So in my opinion the 1 Ghz G4s values are not too bad under Linux.

I will test this on a 1.25 Ghz Mac mini G4 running Linux later today and update the results.


**Update:**
On the Mac mini (1.25 Ghz G4 with Debian testing) it is around 1.50 secs per cycle when using -O and around 1,41 secs per cycle when using -02 optimization (-03 makes no difference again)

cu
APU

---

### Post by miniteg on 2007-04-04
Hello,

Thank you guys for your input.

So my machine is indeed running at optimal speed/performance. The "new bogomips" thing tricked me into thinking I had something wrongly configured. 

It looks like the problem comes from imagemagick itself. I'll try and see if forcing the use of 8 bits per channel or removing antialias or even downgrading to version 4 can help bring computing times to a normal value (I'm looking into 4-5 seconds per picture). 

Well, if I'm not too lazy. 'cos I'm doing this Coppermine thing for my own amusement only, so I don't mind waiting 20 minutes every now and then, when I have a new batch of pictures to process...

Thank you,

Teg-

---

