---
title: "Format HardDisk"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-07-08
Cheers,

I mounted a Fat32 Harddisk in my system and now I want to format it as Ext3. How do I do it using the Terminal?

Thanks.

---

### Post by tchoklat on 2007-07-08
unmount it with the umount command then launch GPartEd and reformat it I guess!

---

### Post by delphiguy on 2007-07-08
yeah but gparted does not work with Terminal.  Or maybe I'm wrong.

---

### Post by nvteighen on 2007-07-08
First, do you have GParted installed? For some weird reason, you have it in the Live CD, but then it isn't automatically installed in the system...

To install it:
```

sudo apt-get install gparted

```

To start GParted you can go to the System Menu -> Administration... or just type the following at the terminal:
```

gksudo gparted

```

To do anything with partitions you always have to unmount your "target" first. You can do that in GParted (right clicking the desired partition or something similar... just look at the menus). After it is unmounted, you are able to format the partition (Format as..., again, I don't remember well where is it exactly... and I'm not able to boot Ubuntu right now).

Good luck!

---

### Post by delphiguy on 2007-07-08
Thanks for the help guys. I have found this link that does exactly what I needed.
[http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml)

---

