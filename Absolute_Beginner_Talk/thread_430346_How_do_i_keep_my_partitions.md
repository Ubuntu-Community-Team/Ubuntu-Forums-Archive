---
title: "How do i keep my partitions"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by LauH on 2007-05-02
Hey everyone. I'm clean installing 7.04 on my pc, but I don't know how to keep my two windows partitions without deleting or formating them. I think it was alot easyer in 6.10.
HDA1 is a fat32 which I don't want to touch.
HDA2 is a NTSF where my windows is installed
HDA3 is where my Ubuntu 6.10 is booting from right now (root), but i want to boot 7.10 from it instead
HDA4 is my swap.

But what should I do in the installer. Here's a screenshot:
[[img]http://www.Photo-Host.org/thumb/627475screenshotda5.png[/img]]("http://www.Photo-Host.org/view/627475screenshotda5.png")

---

### Post by fakie_flip on 2007-05-02
Do not format the partitions you want to keep, and you will still have them. Most people warn that you should backup first, or at least backup the files that you don't want to risk losing. Delete the ext3 partition, and use the free space that you get from deleting it  on your hard drive to install Ubuntu 7.04. You will lose everything on it when you do that. That is where your Ubuntu 6.10 is installed, and you want to replace it with Ubuntu 7.04.

---

### Post by enzobelmont on 2007-05-02
just format /dev/hda3 and mount as / ,of course you will lose its data, you can backup the important data (if you have)  in your fat or ntfs partitions before.

sorry my english... :)

---

### Post by LauH on 2007-05-02
Can't I just install it on the right partitions without touching the others like in 6.10?

---

### Post by enzobelmont on 2007-05-02
yes you can but it will left behind the previous data of /dev/hda3, it contains maybe a lot of useless files, just mark that partition to format and the others will stay safe.

sorry my english... :)

---

### Post by LauH on 2007-05-02
So if I format HDA3 I can install it on it. But what should I set HDA1 and 2 to? boot windows or dontuse

---

### Post by enzobelmont on 2007-05-02
just mark /dev/hda3 for format it, also you can change /dev/hda2 and /dev/hda1 mount point pressing edit partition button.

be sure TO DO NOT MARK your windows partition for format and they will stay safe.

sorry my english... :)

---

### Post by LauH on 2007-05-02
I don't understand what you mean sorry.

---

### Post by ubnewbie2 on 2007-05-02
> **LauH said:**
> So if I format HDA3 I can install it on it. But what should I set HDA1 and 2 to? boot windows or dontuse

I think, if you leave them alone, it will default to mounting each one when 704 boots, under /media/disk1, /media/disk2 etc.

Just mark the one you want 704 to be installed on, to be the root (/) and I am fairly sure it will force you to format it.  All the others will just be entered into fstab, and mounted at boot time

---

### Post by enzobelmont on 2007-05-02
> **ubnewbie2 said:**
> I think, if you leave them alone, it will default to mounting each one when 704 boots, under /media/disk1, /media/disk2 etc.

Just mark the one you want 704 to be installed on, to be the root (/) and I am fairly sure it will force you to format it.  All the others will just be entered into fstab, and mounted at boot time


sorry my english is very limited :lolflag: thats what i mean to say.

---

### Post by enzobelmont on 2007-05-02
sorry i'll go to sleep (3 AM here)

good luck.

---

