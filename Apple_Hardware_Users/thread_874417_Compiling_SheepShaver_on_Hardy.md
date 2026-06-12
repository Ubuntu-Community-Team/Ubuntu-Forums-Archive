---
title: "Compiling SheepShaver on Hardy"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by mfox on 2008-07-29
I have Hardy installed on my G4 PowerBook Al, and since Mac-on-Linux won't run on this kernel, I tried the next best thing, SheepShaver, which can at least run MacOS9.  I originally got instructions for doing this on the FAQ, but this gave me a lot of errors.  I next tried the instructions provided by Gwenole Beauchesne on the [Official SheepShaver Home Page]("http://sheepshaver.cebix.net/"), which involves downloading BasiliskII (a related emulator for earlier versions of the MacOS), making links between the two programs and then doing a Make.  The Make stopped me: here is the output:

Configuration done. Now type "make". 
mfox@mfox-PowerBook:~/SheepShaver/src/Unix$ make 
g++ -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -c main_unix.cpp -o obj/main_unix.o 
main_unix.cpp: In function ‘void sigsegv_handler(int, siginfo_t*, void*)’: 
main_unix.cpp:1654: error: non-local function ‘bool Screen_fault_handler(sigsegv_handler(int, siginfo_t*, void*)::sigsegv_info_t*)’ uses local type ‘sigsegv_handler(int, siginfo_t*, void*)::sigsegv_info_t’ 
make: *** [obj/main_unix.o] Error 1 

Can anyone interpret this error and tell me what to do about it?

By the way, I also compiled BaskiliskII and this gave no problems.  The old System 7.5.2 runs lightning fast on Basilisk, but it can't run PowerPC programs.

---

### Post by wenzhi on 2008-08-02
:KSWelcome to visit our website:[www.jordan9.com](www.jordan9.com)
Please contact e-mail: [email]jordan9@hotmail.com[/email].
We provide the tunnel the product, the preferential benefit price and the warm service.
We hope to get  a good long business time with all customers all over the world.
China Grand Shoes Company is a limited  footwear enterprise company which combine footwear trade with footwear manufature. We have the better despend ,strongpoint and quality than the other manufacturers, we  also brought the best production equipments, technologies, and professionals from abroad. 
We produce over 800,000 shoes per year .
We also can offer kinds of athletic shoes, recreational shoes, stogy, mainly Nike,
adidas, timberland, gucci,prada, Luie Vuitton, puma shoes, Nike Jordan series, Airmax and Shox that let you choose and see.thenFor example:
nike air max 95, airmax 97,
airmax 2006, 
shox TL, 
shox R4,
Shox NZ, 
Air force one(AF1),
Dunk, Kobe,James and so on.If you want to know further information , Please contact to us.I look forward to hearing from you,good luck!

---

