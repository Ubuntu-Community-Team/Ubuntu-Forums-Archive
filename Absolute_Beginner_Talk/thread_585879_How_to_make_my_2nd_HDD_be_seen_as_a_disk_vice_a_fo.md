---
title: "How to make my 2nd HDD be seen as a disk vice a folder"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by electronbee on 2007-10-21
I got the guy mounted and I can access it now (YAY!) but I would like to know how to make it appear as a disk. Also, the mechanism behind how Ubuntu can see a HDD as a folder or HDD.

I'm more curious than anything.

Thanks.

eb

---

### Post by loganm10 on 2007-10-21
the way linux works in this respect is very different from windows

every drive you have is mounted as a folder, there is no other way

your main drive is mounted on "/" or the root directory

and other drives get mounted inside /media, like /media/disk would be one

you can change where they get mounted too, but that is a little more advanced

---

### Post by Roofie on 2007-10-21
Here is a good guide for that ```
http://www.psychocats.net/ubuntu/mountlinux
```

---

### Post by electronbee on 2007-10-21
lohanm,

yes, that is different than the way Windows works. And, it helps. I originally had a lot of frustration but now that bit actually helps.

Roofie,

I used that page to mount my drive. Very helpful!

Now, if only something like that to get my 8600GTS working... :(

I assume I can make my other HDD show up in places with a shortcut?

---

### Post by HermanAB on 2007-10-21
You can also glue a bunch of disks together using a virtual volume, or turn them into a redundant array.  So you can graft storage space on wherever it is needed.

---

### Post by cfaulkner on 2007-10-21
Herman, don't say stuff like that, Raids scare me on consumer machines... lol

---

