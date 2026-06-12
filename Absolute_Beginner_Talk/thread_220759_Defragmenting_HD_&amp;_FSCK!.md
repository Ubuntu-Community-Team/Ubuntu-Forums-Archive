---
title: "Defragmenting HD &amp; FSCK!"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-07-22
hehe sorry for the "!" at the end of fsck. :mrgreen:

anyway i'm wondering if there is a tool to defragment my ext3 linux partition... is fragmentation possible on a linux system? using an ext3 FS? or am i being a knob? i head it was the former and that no defraging is necessary on linux.

anyway... i wanna run fsck on my root (hehe fsck & root :lol:) but a message says it could cause "severe damage to do this on a mounted system" if so is there a way to run this? a special boot up option so it can be run?

cheers

---

### Post by SkyNet2029 on 2006-07-22
Well, there are two ways to go about this...
Sort of.
One way is to force a crash on your filesystem (hard-boot or something of the likes) so as not to allow the journals to get that last five seconds of change-data written down. This would force a file-system check at the next boot. 
The (more rational and Sane ) other way would be by forcing a file-system check by using
```
$ sudo tune2fs (OPTIONS) devicename
```
to change the number of system boots before a specified device is error-checked.
see the man (8) page for full how to 
```
$ man tune2fs
```

Yes, a journalized fs is still capable of fragmentation although not to any extent that you would even need to worry about it or use an app for it. There are a few applications to do a defrag run on such file systems. 
IMHO, these applications only exist for the sake of getting that last dollar out of a former windows user. Old habits die hard I suppose.

---

### Post by ProjectGod on 2006-07-22
That was QUICK. thanks for the feedback. :D

---

### Post by mrvw0169 on 2006-07-22
I agree fragmentation is not generally a problem, but if you do a lot of BitTorrenting and forget to set the "pre-allocate files before download" option, your HD WILL get fragmented on ext3 at least... I remember I forgot this and I always download to 0 bytes free :D so fsck was saying something like 98% non-contiguous files and you can HEAR the HD dying =P

---

