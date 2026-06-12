---
title: "feisty question"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-06-07
I have a question. With the feisty relese of Ubuntu, my dad says he thought he read somewhere that if feisty updates itself, it renames the hard drive from hda to something else and stuffs it up. My mate recently bought a feisty ubuntu dvd of a magazine. Is the true? My mate wants me to come over and set up his ubuntu machine. Ive got dapper, any pointers for feisty.

---

### Post by Najand on 2007-06-07
You mean UUIDs? Or the bug that recognice IDE harddisks (hda) as SATA (sda)? If you mean UUID, there is nothing to be worried about. Have a look at: [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)
If you mean the bug, it does not always happen and it can be fixed easily. So just try it.

---

### Post by steve.horsley on 2007-06-07
When I first installed Feisty, it recognised the hard disk as /dev/sdsa where all previous versions saw /dev/hda. This change in behaviour was undone in the latest kernel update, so my disk has gone back to being hda.

For a normal Feisty install, I don't think this matters because the disks are recognised and mounted using their disk labels not the device names (the file /etc/fstab contains entries starting witu UUID= instead of /dev/). 

However, I had already been in and edited fstab to use the device names instead, so in my case the upgrade broke my installation. Once I took note of the error message from fsck that said /dev/sda didn't exist, it wasn't hard to look in /dev and discover hda there instead, and then edit /etc/fstab to match. But this problem ws only because I had manually changed /etc/fstab in the first place.

---

### Post by Najand on 2007-06-08
That bug has been fixed for Kernel 2.6.20-16-386.

---

