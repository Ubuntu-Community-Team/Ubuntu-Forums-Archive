---
title: "How to write in QNX filesystem"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by apuicewing on 2007-06-19
Hello,

I have a compactflash disk (SanDisk 128 MB), which was formated in QNX4 file system. There are some certain things in the disk which I want to edit. Altough I can mount it and read the files, I can't save them after I modify them. The disk mounts read only.

I've copied all of the disk to a local folder, then formated the the disk to FAT32 filesystem. All was gone, but now I can write in it and save them correctly.

How will I do that in QNX format?

Is it something about not having "mkfs.qnx" in sbin folder ??

Regards,
Alper

---

### Post by rich.bradshaw on 2007-06-19
What the hell is QNX? It's not even on Wikipedia!

Theres a driver here [http://qnxfs.narod.ru/](http://qnxfs.narod.ru/), not sure how you will install it/use it though...

---

### Post by mjwhitfield on 2007-06-19
[http://www.qnx.com/](http://www.qnx.com/)

it's an RTOS used by hospitals and such.  I used it years ago, as it used to boot and work from a floppy disk.

---

### Post by mjwhitfield on 2007-06-19
> **rich.bradshaw said:**
> What the hell is QNX? It's not even on Wikipedia!yes it is:
[http://en.wikipedia.org/wiki/Qnx](http://en.wikipedia.org/wiki/Qnx)

---

### Post by apuicewing on 2007-06-19
So I guess there is no easy way to do it??

Thanks for the link rich.bradshaw, but I've already tried it. It tells to modify a phrase in /usr/lsrc/inux/include/linux/fs.h but I couldn't even find it  in that file.

---

### Post by lank23 on 2007-09-16
I did have this driver working before on an older 2.4.x kernel machine, but seems that it will not compile on a 2.6.x machine that easy still have lots of errors to work out.

---

