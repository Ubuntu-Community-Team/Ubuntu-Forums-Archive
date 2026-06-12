---
title: "Should I install 6.10?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-12
I recently received the shipit cd I ordered when I was thinking of installing Ubuntu, and to my surprise it was a 6.10 Live CD(with free stickers:)).  I want to install it to get the newer repositories, etc.  Is there anything particularly buggy in 6.10 that I should be aware of?  Also, what's the terminal command to list my partitions and their mount points?

---

### Post by ciscosurfer on 2007-03-12
> **Matt1632 said:**
> I recently received the shipit cd I ordered when I was thinking of installing Ubuntu, and to my surprise it was a 6.10 Live CD(with free stickers:)).  I want to install it to get the newer repositories, etc.  Is there anything particularly buggy in 6.10 that I should be aware of?  Also, what's the terminal command to list my partitions and their mount points?With the full release of Feisty about to come out, I would say that yes, you should probably upgrade to Edgy.  Some people have some problems with it (you'd have to search the forums for specifics, sorry) but most people find that it is stable.

The commands to list your partitions is```
sudo fdisk -l
```That's a lower-case "L"

The commands to show your mount points```
cat /etc/fstab
OR
cat /etc/mtab
OR
mount
_*TO MODIFY YOUR MOUNT POINTS, YOU HAVE TO SUDO INTO THE /etc/fstab file
```*_

---

### Post by Matt1632 on 2007-03-12
Ok, I think I will install 6.10, I've become competent enough to fix some of my problems, so it doesn't need to be perfectly stable.  Also, did shipit just start shipping 6.10 cds?

---

