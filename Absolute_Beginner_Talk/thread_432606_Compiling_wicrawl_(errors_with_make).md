---
title: "Compiling wicrawl (errors with make)"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by matt_heys on 2007-05-04
I am having a problem using make to compile and install wicrawl, below is the bit I think is the error message, it appears to be problems with wireless.h and discovery.h

I have attached the complete output from the console incase you need more, also I have done the advised bit of installing it's dependencies by doing "sudo apt-get install libpcap0.8-dev libxml-smart-perl libgtk2-perl libssl-dev"

Realy scratching my head on this, I'm technically adept but a Linux Newbie, any help will be really appreciated, hopefully I will learn something new from this and not need to ask again.

make[1]: Entering directory `/home/mjh/Desktop/wicrawl-0.3a/util'
cc -g -Wall -I../include -I.   -c -o errlib.o errlib.c
In file included from ../include/wicrawl.h:79,
                 from errlib.c:1:
/usr/include/linux/wireless.h:646: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:659: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:684: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:700: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:713: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:740: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:802: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:838: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:847: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:859: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:882: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:897: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:941: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1042: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1060: error: expected specifier-qualifier-list before ‘__u16’
In file included from ../include/wicrawl.h:96,
                 from errlib.c:1:
../include/discovery.h:109: warning: ‘packed’ attribute ignored for field of type ‘uint8_t[16]’
../include/discovery.h:110: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:111: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:112: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:113: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:114: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:115: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:116: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:117: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:118: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:119: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
make[1]: *** [errlib.o] Error 1
make[1]: Leaving directory `/home/mjh/Desktop/wicrawl-0.3a/util'
make: *** [wicrawl] Error 2

---

### Post by jfinkels on 2007-05-05
I don't know where you got this source package from, but for the most part, the process for compiling a program from source looks like this:```

tar xzvf foo-X.Y.Z-i386.tar.gz
cd foo-X.Y.Z
./configure
make
sudo make install

```

Did you need to do ```
./configure
``` before running make?

---

### Post by matt_heys on 2007-05-05
Thanks for the reply, there was no configure file in the directory.

I tried it anyway in blind hope it would work, but it didn't.

There was only the Makefile and a few directories.

---

