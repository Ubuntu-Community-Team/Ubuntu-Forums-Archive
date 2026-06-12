---
title: "Invalid Signature when trying to boot Lubuntu (Dual Boot)"
date: 2014-09-14
forum: BSD
---

### Post by linuxyogi on 2014-09-14
Hi,

After installing ZFS support in Lubuntu using the ZFS PPA I installed PCBSD using available free space. After installation I found that PCBSD's grub has overwritten Ubuntu's grub but Lubuntu was not detected.

So I manually added an entry for Lubuntu in /usr/local/etc/grub.d/40_custom.```
cat /usr/local/etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "lubuntu" {
    set root='(hd0,1)'
    chainloader +1
    }


```


```


 	   	fdisk ada0
******* Working on device ada0 *******
parameters extracted from in-core disklabel are:
cylinders=310101 heads=16 sectors/track=63 (1008 blks/cyl)

Figures below won't work with BIOS for partitions not in cyl 1
parameters to be used for BIOS calculations are:
cylinders=310101 heads=16 sectors/track=63 (1008 blks/cyl)

Media sector size is 512
Warning: BIOS sector numbering starts with sector 1
Information from DOS bootblock is:
The data for partition 1 is:
sysid 131 (0x83),(Linux native)
    start 2048, size 48828125 (23841 Meg), flag 0
	beg: cyl 0/ head 32/ sector 33;
	end: cyl 1023/ head 254/ sector 63
The data for partition 2 is:
sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
    start 48830464, size 255858688 (124931 Meg), flag 0
	beg: cyl 1023/ head 254/ sector 63;
	end: cyl 1023/ head 254/ sector 63
The data for partition 3 is:
sysid 130 (0x82),(Linux swap or Solaris x86)
    start 304689548, size 7887157 (3851 Meg), flag 0
	beg: cyl 1023/ head 254/ sector 63;
	end: cyl 1023/ head 254/ sector 63
The data for partition 4 is:
<UNUSED>
```






I noticed that update-grub or update-grub2 doen't work under BSD but after reboot I saw the entry for Lubuntu but I select lubuntu and press enter I get

```
'Error: Invalid Signature'
```

How to solve this ?

---

### Post by Elfy on 2014-09-14
*Thread moved to **Other Operating Systems and Projects**.*

---

