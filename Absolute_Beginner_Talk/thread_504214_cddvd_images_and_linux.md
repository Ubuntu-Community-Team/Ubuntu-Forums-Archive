---
title: "cd/dvd images and linux"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by deerant on 2007-07-18
A simple question (with a simple answer i hope):

How do i mount images in linux? I mean not just iso's but bin's ccd's or bwt's (the later really interests me)

Is there way or do i have to convert them to other types using windows?

---

### Post by trak87 on 2007-07-18
```
sudo mount cd.iso -r -t iso9660 -o loop /media/some_mount_point
```

where cd.iso is your image and some_mount_point is a directory you create first before running the above.

And then unmounting:

```
sudo umount /media/some_mount_point
```

Note that the command for unmounting is umount, and not uNmount.

---

### Post by Happy_Man on 2007-07-18
Yes.... it is called AcetoneISO, and it can mount almost anything: [http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)

---

### Post by deerant on 2007-07-18
thanx acetonISO seems to do the trick

---

