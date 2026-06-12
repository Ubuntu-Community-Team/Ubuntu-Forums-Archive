---
title: "RePartitioning?"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Alpha_Cluster on 2005-09-27
Is there a way to split a made partition on a hard drive without reformating? Or do i need to reformat my inter drive? And eather way is there a dual boot program that comes with ubuntu?

---

### Post by mlomker on 2005-09-27
Ubuntu includes **grub**, which is a good boot manager.  The Breezy installer can resize paritions but Hoary doesn't.  A Knoppix liveCD would have a copy of [qparted]("http://qtparted.sourceforge.net/screenshots.en.html") on it that you could use.

I'd definitely back your stuff up first, regardless.

---

### Post by Alpha_Cluster on 2005-09-27
Ok thanks how ironic i have a Knoppix LiveCD sitting right next to me. :)
But i cant find a way to get it to redo the sizes without reformating?

---

### Post by matthewv on 2005-09-27
You need to use qtparted to resize your windows partition, to make some free space at the end of your drive. Then you can create linux partitions in this free space

---

### Post by Alpha_Cluster on 2005-09-27
windows is not installed anymore.  I have ubuntu running is there a way i can change that partition.

---

### Post by matthewv on 2005-09-27
Is the resize option available on your linux partition, in qtparted???

---

### Post by Alpha_Cluster on 2005-09-27
No that is my problem. :(

---

### Post by matthewv on 2005-09-27
The Breezy live cd includes gparted, which can resize ext3 partitions. I don't know whether gparted is on the Hoary live cd.

---

### Post by mlomker on 2005-09-27
>  I don't know whether gparted is on the Hoary live cd.

It isn't.  That's a new feature of the Breezy installer.  As is the ability to format a reiser partition, my personal preference.

---

### Post by erikpiper on 2005-09-27
Gparted cannot modify mounted partitions. Boot knoppix or something with gparted from a cd. Modify partitions from there.


THANKS! I finnaly found a qparted alternative for ubuntu! gparted! YES!

---

### Post by matthewv on 2005-09-27
[QUOTE=erikpiper]Gparted cannot modify mounted partitions. Boot knoppix or something with gparted from a cd. Modify partitions from there.
[/QUOTE]

That's why you use the breezy **live** cd:)

---

