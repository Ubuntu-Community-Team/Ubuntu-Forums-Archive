---
title: "is my disk thoroughput low??"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-01-29
ive attached my bootchart which says what my disk thoroughput is, can you tell me if its low? 26mb dosent seem much.

thanks

---

### Post by dstew on 2008-01-29
It is probably 26 megabytes per second = 26*8 = 208 megabits per second. Sounds pretty fast, but maybe others have more info??

---

### Post by Whiffle on 2008-01-29
Sounds low to me.  My 5 year old computer with regular PATA drives gets 55 MB/s via hdparm.  Just so we're using the same measurement, run 

sudo hdparm -tT /whatever/your/hard/drive/device/is

and then we'll have a better comparison.

---

### Post by skymera on 2008-01-29
ok thats quite shocking.

This is a new 10,000rpm drive =|

i'll have to do that hdparm thing when im next on ubuntu :wink:

---

### Post by Whiffle on 2008-01-29
You got me curious...so i installed bootchart.  Here it is on my T43 thinkpad, 120 GB 5400 rpm seagate momentus.  The number it gives me is the same as what hdparm gives me.  I'd say you've got a driver issue, ubuntu probably has the wrong driver for your chipset.

---

### Post by skymera on 2008-01-29
o wow.
thats a lot higher than mine and thats on a 5.4k!

so does anyone know of any issues with the raptor 10k on ubuntu?

---

### Post by Whiffle on 2008-01-29
I doubt the problem is the drive itself, but the ide or sata controller on your motherboard.  Ubuntu probably has either the wrong driver for it, or the right driver and its just being "safe."  You can find out more info about what you've got with the lspci -v command, it should list something like IDE Controller or SATA controller, like this:

```

root@blacktop:/home/andy# lspci -v

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: IBM Unknown device 056a
        Flags: bus master, 66MHz, medium devsel, latency 0
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Capabilities: [70] Power Management version 2



```

With that info you should be able to figure out what driver it needs and force the loading of that driver, or possibly just use hdparm to enable the right options for the driver its using.

---

### Post by skymera on 2008-01-29
```
 00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
        Subsystem: Dell Unknown device 01dd
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fec0 [size=32]
        Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 

```

any use?

---

### Post by skymera on 2008-01-29
and the hdparm

```
scott@scott-desktop:~$ sudo hdparm -tT /dev/sdb
[sudo] password for scott:

/dev/sdb:
 Timing cached reads:   2308 MB in  2.00 seconds = 1154.10 MB/sec
 Timing buffered disk reads:  240 MB in  3.03 seconds =  79.21 MB/sec
scott@scott-desktop:~$ 


```

but i get very diifferent results if i just do 't' without the first T

```

scott@scott-desktop:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:   58 MB in  3.06 seconds =  18.93 MB/sec
scott@scott-desktop:~$ 

```

why is the second so low?

---

### Post by skymera on 2008-01-30
is this any help?

---

### Post by skymera on 2008-01-31
anyone have any thoughts?

anything is much appreciated :)

---

