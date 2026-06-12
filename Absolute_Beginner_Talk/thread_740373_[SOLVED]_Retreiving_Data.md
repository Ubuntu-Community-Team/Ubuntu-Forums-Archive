---
title: "[SOLVED] Retreiving Data"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Humanities Major on 2008-03-30
Hi, I probably have to reset my system to factory default.  I want to try to retrieve my files while in the Live CD, but they don't show up.  I can go into the filesystem, then the home folder but the only account that shows up is ubuntu.  Any idea where on the system my files m ight be hiding?

---

### Post by forestpixie on 2008-03-30
They'll be hiding inside /media - the filesystem is the live cd - open /media nad you're partitions should be in there.

---

### Post by annda on 2008-03-30
Hi,

if i understand right, you have ubuntu installed on you hard disk. if so, first you will need to mount the disk using the terminal:

```
sudo fdisk -l
```

will tell you what your disk partition is called. for example, if it's sda1:
```

sudo mkdir /media/any_name_you_like
sudo mount /dev/sda1 /media/any_name_you_like
```

now you will be able to find your user files in /media/any_name_you_like/home/your_username

hope this helps

---

### Post by Humanities Major on 2008-03-30
Thank you so much, after trying every partion, I found all my files!

---

