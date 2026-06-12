---
title: "Write permission denied on new external drive"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by dhar2112 on 2007-06-28
I formatted a new external usb drive (ext3) for mp3s, pictures, etc....I attempted to drop some files into it and was denied because I don't have write permission.  The owner is listed as "root - root," so I would assume I need a command to change that, correct?  The drive is /dev/sdb1.

Thanks much!

---

### Post by trak87 on 2007-06-28
Open a terminal, go to that drive and create a new directory and make yourself the owner:

```
cd <whatever_the_mountpoint_is>
sudo mkdir mystuff
sudo chown yourlogin:yourlogin mystuff
```

Now you can put anything under the mystuff directory.

---

