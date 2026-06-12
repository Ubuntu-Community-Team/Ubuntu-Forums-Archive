---
title: "Accessing the HDD while running Ubuntu from the CD?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by grs on 2007-04-27
I have Ubuntu installed on HDD but I seem to have damaged something while tinkering with files and now it won't boot right. There are a few files I would like to get that I had saved on the Desktop before I reinstall Ubuntu. If I boot from the unbutu CD how can I access the HDD and copy the files off the HDD?

---

### Post by lamalex on 2007-04-27
open up a terminal
```

sudo fdisk -l
(look and see what your drives are labeled as, hda1, hdb1, sda1, sda2, that sort of thing)
sudo mkdir /media/hda1
sudo mount /devhdXn /media/hda1

```
now go nuts!

---

### Post by grs on 2007-04-27
I typed

sudo fdisk -l

And I got

Disk /dev/hda

Then I was able to make the directory but when I typed the last line I got

mount: special device /devhdXn does not exist

What does that mean, how do I get around this problem?

---

