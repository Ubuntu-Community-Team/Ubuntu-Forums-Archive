---
title: "XWAX a Serato Scratch program for Linux"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by _Darm on 2007-05-26
I found this program [http://www.pogo.org.uk/xwax/](http://www.pogo.org.uk/xwax/) that does a great thing.
I downoaded it but it doesn't work.
When I am trying to start it it says
main@main-desktop:~/xwax-0.1$ ./xwax -t serato_2b -i xwax_import -l ~/music -l cdtracks -d /dev/dsp -d /dev/dsp1
./xwax: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
main@main-desktop:~/xwax-0.1$ 
But I downloaded panzer game that uses Lib SDL and it works just fine
I was also wondering if anyone can add it to main repository?

---

### Post by peachy on 2007-05-28
Hi, install libsdl-ttf2.0-0, it's in the repositories.

I haven't got it working yet, I've tried:
./xwax -t serato_2b -i xwax_import -l ~/Music -d /dev/dsp -d /dev/dsp1

(my music dir is Music)

It scans everything then ends in:
Initialising deck 0 (/dev/dsp)...
Initialising deck 1 (/dev/dsp1)...
open: No such file or directory


I'll keep trying, let me know if you get it working

---

### Post by _Darm on 2007-06-05
It doesn't work on my computer. still.
I was wondering if it is possible to include xwax build for ubuntu in main repositories, or maybe even with next ubuntu studio

---

