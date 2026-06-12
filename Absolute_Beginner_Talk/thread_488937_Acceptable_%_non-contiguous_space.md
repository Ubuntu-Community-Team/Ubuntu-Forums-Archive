---
title: "Acceptable % non-contiguous space"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-06-30
I was watching the disk check on bootup, and the results were:

root: <1%
home: 3%
additional (multimedia) partition: 7.6%

So what's "normal" ?

---

### Post by angryfirelord on 2007-07-30
I don't think there is a "normal" amount. As long as the issue is fixed, then you're ok.

Now if it said something like 25%, then I'd be a little concerned.

---

### Post by Nekiruhs on 2007-07-30
Below %15 is about average. I woulden't worry about it though, because Ext3 Filesystem rarely gets badly fragmented until its above %95 full.

---

### Post by asmoore82 on 2007-07-30
and even if ext3 does become fragmented, you DON'T have to worry about it bonking any of your data.

experts say that in modern OSes, fragmentation can't really slow you down;
your hard drive is already handling multiple read/writes requests to multiple locations
if you are using your computer for more that 1 task at a time.

---

### Post by kostkon on 2007-07-30
I heavily used my ext3 partition for 2 years and all I got was 3%, so I tend to believe that ext3 does not get fragmented easily. Your numbers look fine to me :)

---

### Post by raven on 2007-08-01
I need your opinions
I have my hard disk of 300GB Hard disk shows on boot that it is 26% non-contiguous on my home partition and yes I do copy and delete large files for almost 2 years on the same hard disk

/boot 1GB
/root 10GB
/swap 2GB
/home 280GB

1-is it bad ?
2-what can I do ?

Thanks

---

### Post by Sayers on 2007-08-01
how "would" you defragmentate it ?

---

### Post by bodhi.zazen on 2007-08-01
You do not need to defragment. Linux != Windows

This is the "classic"

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Cene on 2007-08-01
A bit offtopic: Why the hell do you have 1gb /boot?
I've got 16mb /boot and it's never even near being full; 9mb used when i got 4 different kernel builds (and grub of course) there..

---

### Post by FleetAdmiral74 on 2007-08-01
> **Cene said:**
> A bit offtopic: Why the hell do you have 1gb /boot?
I've got 16mb /boot and it's never even near being full; 9mb used when i got 4 different kernel builds (and grub of course) there..

lol, just lots of overhead maybe? You know like in ext3, it has the overhead built in so no need to defrag.

maybe he just took this whole concept...a wee bit to far. :lolflag:

---

