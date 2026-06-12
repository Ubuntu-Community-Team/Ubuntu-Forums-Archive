---
title: "[help] file/folder sharing with windows"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-09
Hi,

I'd like to share ubuntu files/folders with windows xp/vista
and vice versa; i.e. windows files/folders with ubuntu.

Where do I start in christian edition 3.2?

Thanks.

---

### Post by FleetAdmiral74 on 2007-06-10
Well, I have no idea what you mean by the christian edition 3.2....

but assuming you are using ubuntu...just boot up a gParted or LiveCD and use the partition editor to create a FAT32 partition (might need to resize existing). Both Linux and Windows will be able to read and write to this.

---

### Post by pcandpc on 2007-06-10
Hi,

Thanks.

Well, christian edition 3.2 is ubuntu 7.04, I think.

And, what I meant was networking this ubuntu
and windows, not creating fat32 partition.

---

### Post by freebeer on 2007-06-10
Are you trying to share files between the two OSs on the same machine, or are you trying to share them across a network?

---

### Post by pcandpc on 2007-06-10
Hi,

Across the network.

---

### Post by freebeer on 2007-06-10
I've set up a Samba server on Ubuntu to do that.  I followed this HOWTO to get the job done.  [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

