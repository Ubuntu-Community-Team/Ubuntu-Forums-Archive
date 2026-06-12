---
title: "looking for daemon tools 4 linux?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-28
Is there a similar program like daemon tools 4 linux?

---

### Post by ubuntuuser on 2006-07-28
I don't know of any program like that, but I believe it is not necessary under linux. Linux treats everything like some kind of file. That means, even your cdrom /dev/hdc is nothing more than a file to linux, where it can read from (if I said something stupid now, please correct me). So you can just "mount" regular iso files:```
mount -o loop -t iso9660 some.iso /mnt/isoimage/
```This way, the iso will appear in your filesystem just like you have the CD in a drive.

---

### Post by hw-tph on 2006-07-28
Like Ubuntuuser said, loopback mounting works a treat for plain ISO9660 images. I would like to add that [cdemu](http://cdemu.sf.net) works well for mounting and using Goldenhawk-type CD images (.cue/.bin file combos).


Håkan

---

### Post by ricesteam on 2006-08-01
Hi, 

I'm really new to linux, and I can't seem to mount iso described above.

I get this error message:

mount: Not a directory

---

### Post by hw-tph on 2006-08-02
The last argument in the example above, /mnt/isoimage/, is a mountpoint. A mounpoint is the directory where the files will show up and it needs to exist before you try to mount. Create the directory and try again. You will probably also need to prepend the entire command with sudo (sudo mount...).


Håkan

---

