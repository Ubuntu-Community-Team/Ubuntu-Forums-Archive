---
title: "Leopards and Gibbons: A symbiotic relationship?"
date: 2008-03-17
forum: Apple Intel Users
---

### Post by qiemem on 2008-03-17
My friends have convinced to buy a macbook (pro), but I am very much in love with Linux (and Ubuntu) and do not want to give it up.  Thing is, Leopard seems really great and, in particular, as an amateur developer I want access to the cocoa libraries and all that. 

I was wondering if it is possible to dual boot in such a way that OS X and Ubuntu share a home partition.  That way, I could make, say, 10gb root/boot partitions for both OSs and then use the rest of my HD for a single home partition.

If this is not possible, what is the best way to run both OSs on a macbook?

---

### Post by cyberdork33 on 2008-03-17
This is well covered in this forum. Please Search. I wouldn't recommend sharing a home partition though it is possible:
[http://ubuntuforums.org/showthread.php?t=680199](http://ubuntuforums.org/showthread.php?t=680199)
[http://ubuntuforums.org/showthread.php?t=602766](http://ubuntuforums.org/showthread.php?t=602766)
[http://ubuntuforums.org/showthread.php?t=486483](http://ubuntuforums.org/showthread.php?t=486483)

I would rather suggest creating a separate FAT32 partition where information that you want to access under both Ubuntu and OS X can be stored. FAT32 is well supported by both OSs. There is a 4GB filesize limitation to FAT32 though.

Thorough information on installing Ubuntu (in a dual-boot configuration) is in the wiki page for your hardware:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by qiemem on 2008-03-17
Sorry about the redundant post... Don't know why it didn't occur to me to search first :P

Thanks though!

---

### Post by qiemem on 2008-03-17
submitted twice...

---

### Post by cevans on 2008-03-19
I'll add a few points here that weren't noted in the previous threads, since I'm not sure which thread to add them to:

[LIST]
[*]If you modify permissions in any OS, set a root password first, so that you won't have to worry about sudo breaking.
[*]If you use HFS+ or FAT32 as a filesystem, be sure to realize that neither of these will be journaled, and understand the implications of this. A bad unmount or power failure can cause filesystem damage very easily, and sometimes to a major extent.
[*] If you have more of one type of system, it is probably best to change the permissions in the other operating system - I change OS X permissions, for example, since most of my systems run Linux, and I'm uid 1000 on nearly all of those.
[*] If you use hardy, hfsprogs has a version of fsck for hfs+ that works quite well.
[/LIST]

---

