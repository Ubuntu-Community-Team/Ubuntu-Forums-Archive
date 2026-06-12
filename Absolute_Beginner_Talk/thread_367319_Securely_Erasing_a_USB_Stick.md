---
title: "Securely Erasing a USB Stick"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-22
Hi!  I have recently stored some sensitive data on a USB stick, and I would like to securely format it.  From the Windows and Mac world, I know that this requires seven passes to zero out the data.  Could someone please tell me how this is done in Linux?

---

### Post by kidders on 2007-02-22
Hi there,

Assuming I didn't have an app that could do this for me (like shred, maybe), I would do something like **dd if=/dev/urandom of=/dev/whatever bs=<my block size>** a few times, to dump random data onto the device.

I imagine the only reason to do it more than once would be to clear I/O buffers & such.

---

### Post by Darklighter137 on 2007-02-22
Can this program known as "shred" accomplish a secure deletion? ^_^

---

### Post by yabbadabbadont on 2007-02-22
The only truly surefire way to wipe that stick involves a large hammer...  :lol:

(7 or 8 passes of random data is a close second ;))

---

### Post by Darklighter137 on 2007-02-22
:biggrin:

---

### Post by russell.h on 2007-02-22
Actually you have to get it really hot. If someone is determined enough and has the resources they can still get some data from a smashed drive, but if you get it hot enough it will be just plain gone.

---

### Post by Shay Stephens on 2007-02-22
> **kidders said:**
> Hi there,

Assuming I didn't have an app that could do this for me (like shred, maybe), I would do something like **dd if=/dev/urandom of=/dev/whatever bs=<my block size>** a few times, to dump random data onto the device.

I imagine the only reason to do it more than once would be to clear I/O buffers & such.

How do you know what the block size is?

---

### Post by kidders on 2007-02-22
> **Shay Stephens said:**
> How do you know what the block size is?That depends on the filesystem. For Ext2/3, for instance, dumpe2fs will tell you.

> **yabbadabbadont said:**
> The only truly surefire way to wipe that stick involves a large hammer...  :lol:Hehe. That would work ... provided the hammer was for the computer, not the disk!

---

### Post by yabbadabbadont on 2007-02-22
@russell.h
@kidders

It's a USB stick, not a drive...  last time I checked, silicon shatters very nicely.  :D

(Especially if you smash it repeatedly with a 2 pound sledge :twisted:)

---

### Post by bigken on 2007-02-22
[quote=yabbadabbadont;2192780]The only truly surefire way to wipe that stick involves a large hammer...  :lol:

Yep just stamp on it and buy a new 1 :lolflag:

---

### Post by crashtestway on 2007-02-22
same here i got a 1 gb for 14 bones say hello to "sweet lady brick" time lol

---

