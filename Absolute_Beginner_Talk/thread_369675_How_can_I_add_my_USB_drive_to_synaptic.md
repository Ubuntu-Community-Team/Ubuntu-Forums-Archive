---
title: "How can I add my USB drive to synaptic"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2007-02-24
Hi all, how can I get synaptic to recognize my usb drive[sda1] as a cache/repository for doing installs/reinstalls? Any time I update I transfer updates to sda1[vfat] file "ext archives", but then have to transfer back to get synaptic to use. Tried dvd-rw[requires 4] but that gets a little tedious on the catalogue/burning end. Will appreciate any help!

---

### Post by dbbolton on 2007-02-24
it seems that for what you want, you would have to boot from that USB drive.

---

### Post by az on 2007-02-24
Dump all the debs in one directory, cd to that directory and then run

dpkg-scanpackages . /dev/null > Packages

and then you can add the usb stick as a repo by hand:

the line should be something like this:

deb file:/media/MyUsbStick/debs/ dapper main restricted

(You probably will have to put the appropriate names of the repo, it may just be main, or something...)

Also, dpkg-scanpackages is in the dpkg-dev package.

---

### Post by randiroo76073 on 2007-02-25
Thanks az, the part I was missing was:  "dpkg-scanpackages . /dev/null > Packages".  I ended up with: "deb file:/media/EXT 1/linux/ex-archives".  Learning somethin new every day :)

---

