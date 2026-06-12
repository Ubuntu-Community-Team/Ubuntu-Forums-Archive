---
title: "Permissions on Fat32/ext3 drives"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by agiamba on 2007-03-02
Hi, this problem is making me go nuts.

I have two drives, and both of them are read only.

Problem #1- Fat32 on my internal hard drive, about 25gigs or so, and it does not automount. I want it to mount everytime I load up Ubuntu? And when I do mount it, it's read-only and I can't edit it. It won't let me right-click and edit properties. Recommendations?

Problem #2- Fat32 on my external hard drive (I store almost all my data here, movies/music/pictures/etc.) and everytime I plug it in, it automatically mounts. It always reverts to read-only after about 2-3 seconds of loading up, it says I have Create/Delete folder access, but no read/write file access. All I know is I can't delete stuff, move stuff onto it, and it's very frusterating. Help?

---

### Post by aysiu on 2007-03-02
Maybe this link might help?
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by yabbadabbadont on 2007-03-02
Problem 2 seems to be happening to many people lately...  I can't help you there.

For problem 1, please post the contents of your /etc/fstab file and the output of "sudo fdisk -l".

Edit: Doh!  Too slow.  :D  (or you could just read his guide :lol:)

---

### Post by agiamba on 2007-03-02
[PHP]/dev/sdb1 "/media/WD Passport/" vfat iocharset=utf8,umask=000 0 0[/PHP]

That's what I edited into fstab, my folder is WD Passport, and it's mount point is sdb1 as determined here-
[PHP]/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)[/PHP]

When I try to mount everything, it displayed

[PHP] [mntent]: line 12 in /etc/fstab is bad [/PHP]

---

### Post by yabbadabbadont on 2007-03-03
I don't think you can quote a mount point including spaces.  (You're just asking for trouble... ;))

Instead of quoting it, try escaping the space with a backslash.

/media/WD\ Passport

---

