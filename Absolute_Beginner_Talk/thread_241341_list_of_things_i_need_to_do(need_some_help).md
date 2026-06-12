---
title: "list of things i need to do(need some help)"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by econobeing on 2006-08-22
i installed ubuntu onto my dell b130/1300 notebook, it pretty much went without a problem, except for a few things.

1. the resolution was stretched 10x7 and not the 12x8 i wanted, got this one fixed.

2. i can't play mp3s

3. my internal wifi card doesn't work.

as i said, i got the resolution problem fixed, and that's got me pretty hapy right now, now i just need to get the other two problems fixed.

i think problem 2 is the most important right now, because i have a wired connection that i'm using right now, so i can live without wi-fi for a while, but this silence is killing me... any advice?

---

### Post by MaximB on 2006-08-22
1.search the ubuntuforums on "how to"
we've got pleny of this "resolution" issues solved
2.you need to download the CODECS
in the add/remove programs find the codec packs and install them
3.I know about ADSL...but not wifi.
search this forum for more...

---

### Post by econobeing on 2006-08-22
got problem 2 solved, somebody else posted the same question a few topics down :P

i think problem 3 is going to be the biggie...(starts searching)

---

### Post by az on 2006-08-22
What chipset is it?

---

### Post by econobeing on 2006-08-22
chipset?

hmm, i think i remember reading something about that, is it the "info.linux.driver" property? if so mine is "bcm43xx"

[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)

^i was reading those instructions and i got the the "make" part, but make doesn't work, this is what happens when i try:

> 
make -C driver
make[1]: Entering directory `/home/travis/Desktop/stuf/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/travis/Desktop/stuf/ndiswrapper-1.23/driver'
make: *** [all] Error 2


---

