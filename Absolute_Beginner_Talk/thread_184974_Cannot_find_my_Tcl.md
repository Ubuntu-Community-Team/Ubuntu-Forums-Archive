---
title: "Cannot find my Tcl"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by knewmocker on 2006-05-30
I was trying to configure an eggdrop for myself but everytime I try I get the message

 Tcl cannot be found on this system.

  Eggdrop requires Tcl to compile. If you already have Tcl installed on
  this system, and I just wasn't looking in the right place for it, re-run
  ./configure using the --with-tcllib='/path/to/libtcl.so' and
  --with-tclinc='/path/to/tcl.h' options.

now I know it is installed I have Tcl 8.4 nad where it is looking for libtcl.so or tcl.h I cannot find them anywhere. is there somthing I am overlooking?

---

### Post by johnc4510 on 2006-05-30
Try here:/usr/lib/libtcl8.4.so.0

---

### Post by catlett on 2006-05-30
Enter in the terminal ```
whereis libtcl.so
``` It will list the path. You can do whereis with anything else to find its path.

---

### Post by knewmocker on 2006-05-30
I have found the file but everytime I try to do tcllib='usr/lib/libtcl8.4.so.0 all it dose is bring me to a
>
promt and i cant do anything but restart the terminal

---

### Post by knewmocker on 2006-05-31
ok I have tcl 8.4.9 installed right now. if I type whereis for tcl.h or tlibtcl.so I get no returns at all. and even when it auto detects them it tells me now that my version is to old and to download 8.4.6.

Now im no math wiz but im sure 8.4.9 is hire that 8.4.6

I have tried everything I could think of. is anyone else having problems with there tcl other than me?

---

### Post by Xzavier on 2007-09-19
sudo apt-get install tcl8.3-dev

---

### Post by farnoush on 2008-03-12
Try this : ./configure library path=/usr/lib/tcl8.4.
It was surprising! I found this way only by chance! after a lot of hard work when I was so angry I tried to say to Ubuntu to follow the library path that I want. So by a little mixing of english commands and math (!) I told it, what it should do!

---

### Post by dot2kode on 2008-06-29
If anyone is still having a problem with this like I was trying to setup eggdrop.1.16.19 do this:
```
sudo apt-get install tcl8.5-dev
```

Also thanks for the 
```
whereis
```

command :)

---

### Post by forger on 2008-06-29
why not just:
```
sudo apt-get install eggdrop
```
and stick on top of eggdrop.conf this:
> #! /usr/bin/eggdrop

then you just
> chmod +x eggdrop.conf
./eggdrop.conf


You can find the sample here (gzipped):
> /usr/share/doc/eggdrop-data/examples/eggdrop.conf.gz

---

### Post by dot2kode on 2008-06-29
the one in the repo's is not the new version...It's 1.6.18

---

