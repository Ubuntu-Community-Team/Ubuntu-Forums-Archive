---
title: "How to set up a slave drive?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Villa on 2006-11-18
I'm a complete noob, using Ubuntu 6.10 for the first time. I checked out this thread but it's kind of confusing. [http://www.ubuntuforums.org/showthread.php?t=287599&highlight=mount+a+slave+drive]("http://www.ubuntuforums.org/showthread.php?t=287599&highlight=mount+a+slave+drive") but I don't think it applies to me. I don't know how to mount drives, how do you do this?

Basically what I would like to do is mount my slave 80gb drive so I can access it and put stuff on it. It's recognised by the BIOS and everything, I just can't see it or use it in Ubuntu. =( It used to have Windows installed on it, but I wiped it with the Ubuntu bootdisk so I think it's completely wiped. Any help please? I don't know how to use the Terminal in detail, so the easiest way would be best.

Thanks! =)

---

### Post by aysiu on 2006-11-18
Read one of these:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Post any questions you might have.

---

### Post by Villa on 2006-11-18
Should I partition the hard drive? I installed gparted and followed your tutorial up until I tried to mount the HDD. When I tried to I got


wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error


I did the rest of the tutorial, and nothing happened. Am I supposed to allocate the free space in my second empty hard drive before I do anything else? What am I doing wrong?

Thanks. =)

---

### Post by aysiu on 2006-11-18
Well, what format is the drive?

If it's Ext3, you'd follow [this tutorial](http://www.psychocats.net/ubuntu/mountlinux). If it's FAT32 or NTFS, you'd follow [this tutorial](http://www.psychocats.net/ubuntu/mountwindows).

You can, of course, with GParted, reformat the drive to whatever filesystem you want (Ext3, FAT32, or NTFS), but you then have to follow the appropriate tutorial.

After you do that, if it's still not working, post the output here of these three commands: ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

