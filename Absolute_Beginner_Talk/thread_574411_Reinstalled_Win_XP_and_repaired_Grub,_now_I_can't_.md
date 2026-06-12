---
title: "Reinstalled Win XP and repaired Grub, now I can't boot Linux or Windows. Please help."
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by MegaSvensk on 2007-10-12
Hi,

I installed Windows XP again last night after trying Vista for a bit. Then I couldn't boot Ubuntu of course, so I did the root (hd0,1) + setup (hd0) like I've done successfully once before.
But this time something must have gone wrong, because when I try to boot Ubuntu I get this error message:
```
Error 17: Cannot mount selected partition
```
And when I try to boot Windows I get this message:
```
Error 12: Invalid device specified
```

Does anyone know how to solve this problem?

Thanks.

---

### Post by Pumalite on 2007-10-12
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
[http://users.bigpond.net.au/hermanzone/p15.htm#12](http://users.bigpond.net.au/hermanzone/p15.htm#12)
You have XP installed in a logical partition. A no-no. Windows works only from primary partition and likes to be sda1

---

### Post by zvacet on 2007-10-12
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

or 

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

### Post by MegaSvensk on 2007-10-12
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
[http://users.bigpond.net.au/hermanzone/p15.htm#12](http://users.bigpond.net.au/hermanzone/p15.htm#12)

You have XP installed in a logical partition. A no-no. Windows works only from primary partition and likes to be sda1
Thanks for your replies.

No, it is not because all my partitions are primary partitions. Plus Windows did run correctly before I tried to reload Grub.

I think the solution might be in that first link. This:
```
When trying to boot Linux
If you get this error , check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.
For example,
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
But, I'll need some help fixing it.



I already did that, zvacet. Thanks anyway.

---

### Post by ericartman on 2007-10-12
I have fixed error 17 with "Super Grub"
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

lots of info there I wish you luck, it is very time consuming fixing grub errors, has been for me anyway. Probably spent more time on grub errors than anything else involving Linux. (so far)

Cart

---

