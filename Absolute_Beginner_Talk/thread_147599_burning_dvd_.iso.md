---
title: "burning dvd .iso"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by jorn on 2006-03-20
Hi!
I have trouble burning dvd iso files.
Using a "Nec DVD RW ND - 2500"
Same output in GnomeBaker.

```
jorn@ubuntu:~$ growisofs -Z /dev/cdrw=/home/jorn/Sophie.Scholl.2005.PAL.NORDIC.DVDR-CLASSiC/cls-sophie.iso
Executing 'builtin_dd if=/home/jorn/Sophie.Scholl.2005.PAL.NORDIC.DVDR-CLASSiC/cls-sophie.iso of=/dev/cdrw obs=32k seek=0'
/dev/cdrw: "Current Write Speed" is 2.0x1385KBps.
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
         0/4689661952 ( 0.0%) @0x, remaining ??:??
         0/4689661952 ( 0.0%) @0x, remaining ??:??
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...

[1]+  Stopped                 growisofs -Z /dev/cdrw=/home/jorn/Sophie.Scholl.2005.PAL.NORDIC.DVDR-CLASSiC/cls-sophie.iso
jorn@ubuntu:~$


```
I would be glad for some support.
Jorn

---

### Post by taurus on 2006-03-20
Why don't you try out k3b because I do all my burning, CD & DVD, with k3b.  Two thumbs up...  :)

---

### Post by jorn on 2006-03-20
K3B just doesn't work either.
Output: Starting writing speed 2.00x
but nothing happens. No light in the burner.
Jorn

---

### Post by Haak on 2007-12-24
I think I'm about to have the same issues. When I let the application decide (all settings on default "auto" ) this is what happens:

```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
_NEC DVD_RW ND-1300A 1.09 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-RW Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 2.0x1352KBps.
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-! "COMMAND SEQUENCE ERROR"@LBA=0h. Is media being read?
:-! the LUN appears to be stuck at 0h, retrying in 5 secs...
          0/4676200448 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2283301 -dvd-compat -speed=2 -use-the-force-luke=bufsize:32m 
```

Go's on until I kill it. 

Using " ignore"  and DAO options things go well...can't make it a default option inK3B though. 

I think this is a bug?

---

### Post by MrKlean on 2007-12-24
K3B works great for me... If I were you..I would check connections..power and plugs.  Did it just stop wroking..never work..or worked in Windows but not now ??

---

### Post by antler on 2008-03-08
This can be attributed to a problem with the disc that you are trying to burn to. If it's a rewritable, try forcefully formatting it before burning it. Otherwise, try a new disc.

This was the problem for me :-)

---

