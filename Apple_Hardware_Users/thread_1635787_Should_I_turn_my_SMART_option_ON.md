---
title: "Should I turn my SMART option ON?"
date: 2010-12-02
forum: Apple Hardware Users
---

### Post by Symbolix on 2010-12-02
Hi,
* Apple MacBook Pro (A1151, 2006)
* Ubuntu 8.04.4

My last disk failed. It was a mac standard Seagate Momentus 120GB 5400rpm. I have replaced it with a Hitachi Travelex (something), 160GB, 7200rpm. It seems to be all good. However I am now abit paranoid about the HDD health issues. I have installed "smartmontools", in order to be able to keep an eye on my drive's health.

But when I run it:
```
  sudo smartctl -a -d ata /dev/sda3 
```

it goes:
```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTE723216L9A360
Serial Number:    100115FCC200NCJG1R8G
Firmware Version: FC2OC30F
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x42
Local Time is:    Thu Dec  2 14:19:12 2010 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

SMART Disabled. Use option -s with argument 'on' to enable it.
```

Should I do that? Should I enable it? I thought it is ON by default on all modern drives?

Thanks.

---

### Post by Symbolix on 2010-12-04
Any ideas?

---

### Post by MacintoshLover on 2010-12-05
Turing SMART on is always a good idea on hard drives. I've had to deal with at least one computer that had a screwed up hard drive because the person didn't check their disk status/turn on SMART.
     So yes, turn SMART on.:P
P.S. Update your Ubuntu to 10.10. It is awesome! And no, it wont screw up any of your data.

---

### Post by Symbolix on 2010-12-07
Thanks! I will turn it ON then.

Sorry, but I am stuck to this kernel because it is the last one supporting OpenGL with ATI X1600, my mac is an old one, A1151.

I think 8.04 is cool. At least it is rock solid with all the compatible drivers etc.

---

### Post by MacintoshLover on 2011-03-07
> **Symbolix said:**
> Sorry, but I am stuck to this kernel because it is the last one supporting OpenGL with ATI X1600, my mac is an old one, A1151. I think 8.04 is cool. At least it is rock solid with all the compatible drivers etc. Oh. :( Well, at least it works!8-)

---

### Post by kashish on 2011-03-09
ya machuntosh you got the your answere get resolved?

---

