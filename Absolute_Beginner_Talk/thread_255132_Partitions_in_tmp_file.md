---
title: "Partitions in tmp file"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by brucegrr on 2006-09-11
I am a new Ubuntu user and very much a Linux rookie.

Ubuntu is set up in a dual boot environment. Works fine, so far.

Here is the problem I have. The path to my windows partition and to a sata drive I have music on for slimserver is:

/tmp/disks-conf-sda1 and /tmp/disks-conf-hda1

Everything I have read so far says these should be in the media folder. How so I move them? I assume the tmp folder is meant for temporary files and not these partitions? I can browse the partitions fine and Slimserver can acess the sata drive fine but I want them to be in the right place.

Any help is appreciated. Please keep in mind I am as dumb as a pet rock about Linux......Windows.........long time user, computer builder. Linux.....I need help.

Thanks!

Bruce Gerencser

---

### Post by lukew on 2006-09-11
Hay,

Under system admin there is discs appliction.

You can easily change the mount point hrere. Rember you are not changing to physicl location o fthe files only the mount point.

Temp is for temp, I would not put anythig valuable in there. Just incase you sudo rm -r /tmp* :O

I hope this helps.

Luke

---

### Post by anaconda on 2006-09-11
I wouldn't say they HAVE to be in /media folder.

Personally I prefer the /mnt folder.

The difference is that everything that is in media folder is visible in desktop.

But I agree, that /tmp could be dangerous..

---

### Post by brucegrr on 2006-09-11
Thank you for your help.

I suspect this will not be my last visit here. :)

Bruce

---

### Post by monktbd on 2006-09-11
> **anaconda said:**
> The difference is that everything that is in media folder is visible in desktop.


you can set that in gconf-editor for nautilus.
but either on or off for all harddisks.

---

