---
title: "Troubles with grub menu"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Degeim on 2007-03-19
I have almost totally converted to Ubuntu now, but as the title tells us, im missing one thing, and thats gaming support. As I enjoy gaming with my friends now and then, I unfortunately need Windows, and that's where the problems starts.

I had Ubuntu only installed, but of reasons mentioned I had to install WIndows XP, and so I did (on one of my old unused partitions). Now, the grub loader disappeared, but I managed to get it back and continue using my old Ubuntu with the help of [www.ubuntuforums.org/showthread.php?t=224351](www.ubuntuforums.org/showthread.php?t=224351).

But that, of course, did not fix it all. Im now stuck with one unbootable XP, and one perfectly working Ubuntu. I guess the XP can be booted with some knowledge of the grub loader, and thats why I ask here.

After fixing the grub, I had 5 entries; all of them Ubuntu (two different kernels with normal and recovery, and the memory test-thing). I then added
```
title		Windows XP
root		(hd0,X)
quiet
savedefault
boot

```
and tried replacing X with 0, 1, and 2, but all of them gives "Error 8: Kernel must be loaded before booting" (and higher gives, of course, "Error 22: No such partition"). 

Following line shows the partition in /etc/fstab:
```

/dev/hda2   /media/bac   ntfs   nls=utf8,umask=0222   0   0

```

I'm using Edgy.

So; am I doing one very elementary thing the wrong way?

---

### Post by v8YKxgHe on 2007-03-19
You have to load an XP install differently, something like this:

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by al7kz on 2007-03-19
edit

---

