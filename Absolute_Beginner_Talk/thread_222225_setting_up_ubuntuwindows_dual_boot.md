---
title: "setting up ubuntu/windows dual boot"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by carterdea on 2006-07-24
I have a laptop running windows xp. I need to make it dual booting into ubuntu 6 dapper drake. I don't have an idea of what to do because I am a mac man myself thanks
carter

---

### Post by Jagot on 2006-07-24
This guide is for the text based alternate install cd:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And this for the graphical desktop install cd:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by carterdea on 2006-07-24
i know that. But I need a recomendation for a partitioner and a boot up program
thanks

---

### Post by Sef on 2006-07-24
Before you dual boot, **back up** all of your data.  Most of the time there is not problem, but on occassion there is.

---

### Post by Jagot on 2006-07-24
Both versions of the install cd have their own partitioner included and both install the GRUB bootloader for you - you do not need anything else.

---

### Post by aysiu on 2006-07-24
> **carterdea said:**
> i know that. But I need a recomendation for a partitioner and a boot up program
thanks
Theoretically, the Desktop CD can repartition, but I would truth the Alternate CD more.

My personal recommendation for partitioning is DiskDrake (which is available as part of the PCLinuxOS live CD).

---

### Post by carterdea on 2006-07-24
disk drake? and which one is the alternate cd? and why would you "truth" it more?

---

### Post by aysiu on 2006-07-24
Sorry--typo. It should be *trust*, not *truth*.

On the download page, you'll see three ISOs available--one is the Desktop CD, one is the Server CD, and one is the Alternate CD.

The Alternate CD's installer and partitioner is tried and true. I've seen many threads indicating difficulties using the Desktop CD, particularly when it comes to resizing and choosing partitions.

---

### Post by carterdea on 2006-07-24
ok. Awesome thanks. I need to know how to boot from the cd now. Its a Toshiba Satellite Mobile Intel Pentium 4 CPU 3.33 GHZ 1.37GB of RAM and its running Windows XP Proffesional Version 2002 Service Pack 2 (boo!!! ha ha). Wow. Thats a screamin computer. Does anyone know how to boot from CD?

---

### Post by Jagot on 2006-07-24
You'll need to set your BIOS to boot from CD before the hard disk if it is not already set to do so.

---

### Post by carterdea on 2006-07-24
how do I set the BIOS to do that?

---

### Post by Jagot on 2006-07-24
You'll need to enter your BIOS - when you boot up it should give you the key you need to press to access it - it's quite commonly one of the F keys - I think mine's F2.  The layout of the BIOS varies, but you should be able to navigate to the section which handles the devices which are scanned for on boot, then change them accordingly.

---

### Post by genedoc on 2006-07-25
> **carterdea said:**
> Toshiba Satellite Mobile Intel Pentium 4 CPU 3.33 GHZ 1.37GB of RAM and its running Windows XP Proffesional Version 2002 Service Pack 2. Does anyone know how to boot from CD?

My Toshiba will also generate a boot order without entering the BIOS by pressing the F12 key during the initial Toshiba splash screen.  Simply use the arrow keys to move between the various boot options.  Pretty sure the BIOS doesn't need to be changed to use this option.

---

