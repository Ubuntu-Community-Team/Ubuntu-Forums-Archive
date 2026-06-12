---
title: "Defragmenting Ubuntu"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-22
Is it possible to defragment in ubuntu? is it necessary?? Thanks :D

---

### Post by Ozitraveller on 2006-10-22
> **WalmartSniperLX said:**
> Is it possible to defragment in ubuntu? is it necessary?? Thanks :D

It's not necessary, defrag is done automatically every 20 boots.
Defragmentation is rarely more than 2%.

---

### Post by Mimsy on 2006-10-22
Every 30 boots, according to my laptop ;)

No, it's not necesary for you to do anything to defrag. Ubuntu will check your hard drive every 30 boots and take whatever steps necessary. Very convenient.

/Mimsy

---

### Post by WalmartSniperLX on 2006-10-22
Oh I see now. That startup hdd check is a defrag session :D well that IS convenient :D :cool:

---

### Post by mattcn81 on 2006-10-22
Hmmm so what if it's really rare for you to reboot?

---

### Post by blendmaster on 2006-10-22
> Hmmm so what if it's really rare for you to reboot?

I don't know if Ubuntu has something that will allow you to manually do it.

I guess you would have to reboot a lot to get defrag going.

---

### Post by sumguy231 on 2006-10-22
Unless I'm wrong, all that should happen every 30 boots is a run of fsck, which checks (and repairs), not defragments, the volume. ext3 doesn't fragment as easily as NTFS by design. According to Wikipedia, there is no defragmentation utility for ext3 and ReiserFS cannot be defragmented in the first place.

---

### Post by Qrk on 2006-10-22
ext3 is far more resistant to fragmentation than ntfs, so you shouldn't need to check it very much more than once in 20 boots.

If you really want to be sure, the command is fsck, which must be run with sudo.

---

### Post by joshgtv6 on 2006-10-22
searching the synaptic package manager i found a package called defrag, but i'm not sure if it will work.  You can see what filesystems it works on.  Aren't we using a ext3 filesystem?  The text below is the description given

ext2, minix and xiafs filesystem defragmenter
As a file system is used, data tends to become more and more
scattered across the disk, degrading performance.  A disk
defragmenter simply re-organises the data on the disk, so that
individual files occupy a single sequential set of disk blocks,
and all the free space on the disk is collected together in a
single region. This generally means that reading a whole file
is faster, and disk accesses in general are more efficient.

---

### Post by blendmaster on 2006-10-22
A quick Google showed me this Ubuntu forum:

[http://ubuntuforums.org/showthread.php?t=220759]("http://ubuntuforums.org/showthread.php?t=220759")

Hope that's helpful!

---

### Post by mattcn81 on 2006-10-22
That's good to know, because I was having some issues with fragmentation on my Windows XP drive recently. Thanks.


> **Qrk said:**
> ext3 is far more resistant to fragmentation than ntfs, so you shouldn't need to check it very much more than once in 20 boots.

If you really want to be sure, the command is fsck, which must be run with sudo.

---

