---
title: "Fiesty Upgrade Gone Horribly Wrong"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by christo16 on 2007-04-21
Alrighty, so I was using edgy and got a message from the updater asking me if I wanted to upgrade to fiesty.  After completing the upgrade the machine errored out on the restart.  After running fsck -fy off a live cd I get 
```
"wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so"
```

Thank you for any help :)

---

### Post by spin2cool on 2007-04-21
boot into recovery mode and then post the results of "dmesg | tail".  Looking at that log will help diagnose what the problem is.

---

### Post by christo16 on 2007-04-21
Thank you for the reply,
I am unable to boot into recovery mode, GRUB doesn't even see the system any more.  I already installed fiesty on my second drive, I am interested in mounting my second drive so I can pull some data off it.  I ca run fsck -fy and it will find and fix a bunch of things but when ```
"sudo mount -t ext3 /dev/sba1 /media/drive"
``` it pops up that error message in my first post.
thank you!

---

### Post by Sef on 2007-04-21
> ...so I can pull some data off it. 

If you can download Knopppix, then you might be able to get your data off the computer and onto a flash drive.

(Ask a friend if you can download it on their computer.)

---

### Post by louieb on 2007-04-21
> **Sef said:**
> If you can download Knopppix, then you might be able to get your data off the computer and onto a flash drive....
Same with [Puppy]("http://www.puppylinux.org/"). Latest version 130mb download.

---

### Post by christo16 on 2007-04-21
thanks for the replys everyone, I have installed fiesty on my second internal HD, is there some sort of utility I can run inside of fiesty to fix my drive's corruption?
thank you!

---

### Post by christo16 on 2007-04-21
any ideas?

---

