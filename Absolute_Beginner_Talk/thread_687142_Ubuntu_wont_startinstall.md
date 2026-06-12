---
title: "Ubuntu wont start/install"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by winblows.exe on 2008-02-04
I downloaded the Ubuntu Live CD and burned it to disc. Now when I try to install it or boot live, it wont work. I get a bunch of errors showing....

hda: error code: 0x70
sense_key: 0x03 asc:0x02 ascq:0x00
buffer I/O error on device hda, logical block 296595
squashfs error:unable to read page, block240f965b, size 9453


Any ideas with whats going on here?:confused:

---

### Post by spiderbatdad on 2008-02-04
never seen that, but looks like the disk is a coaster. Try downloading the image from another source, check the md5sums, burn the disk (as image, not file) at 4x or less.
Maybe your iso is ok...check the md5sums.

---

### Post by jeffus_il on 2008-02-04
Does you livecd boot? It's not clear from your post. Since you manage to initiate install. If it does boot I would run the partition editor from the livecd to prepare the hard disk before install. You may have a problem with the hard disk.

---

### Post by winblows.exe on 2008-02-04
Yeah, it boots. I get to the Ubuntu screen where the orange bars goes back in forth then the screen goes black and I get them errors. <<?>>

---

### Post by winblows.exe on 2008-02-04
anyone?

---

### Post by spiderbatdad on 2008-02-04
edit: nm leaving this for someone who knows for sure.

---

### Post by spiderbatdad on 2008-02-04
[http://ubuntuforums.org/archive/index.php/t-635056.html](http://ubuntuforums.org/archive/index.php/t-635056.html)

---

### Post by winblows.exe on 2008-02-04
It wont even go live. So I cant do do partitioning. Thanks tho  bro.

---

### Post by oedha on 2008-02-04
have you try install in safe graphic mode ?
~E~

---

### Post by winblows.exe on 2008-02-04
Yes. Sure did. Still a no go.

---

### Post by oedha on 2008-02-04
have you done like what siperbatdad said ?
re-burn your image to another disk in low speed ( 4x )........
i believe it was disk problem

~E~

---

### Post by winblows.exe on 2008-02-04
Right now im downloading the alternate install cd and I will burn it at 4x. Im not worried about booting live because I have worked with ubuntu before on a OEM machine. So any other suggestions? Thanks to all.

---

### Post by jeffus_il on 2008-02-05
Suggestion:
Get your livecd to boot first.
This will indicate to you what Ubuntu doesn't like about your hardware, and make the next steps easier.

Use the grub menu to change kernel boot parameters.
Also your errors are from your harddisk, try disable the disk in bios and boot from the cd.

---

