---
title: "Please, please help: How can I format a drive with the Ubuntu LiveCD?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2008-02-25
I tried to restore a partition from partimage, so the partition was made ext3.  but it has errors, so I want to try again.

I deleted the drive in GParted, and made the partition again using ext3...but it says there is already 1.54gb taken in the partition.  i need t clear before i try this again.  Any way to format it since telling it to "Format to ext3" did nothing?

---

### Post by taurus on 2008-02-25
Can you post the output of this command from a terminal from the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by bodhi.zazen on 2008-02-25
You can use gparted or the command line.

See [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

scroll to bottom of the first post.

---

### Post by gohanssjn on 2008-02-25
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11325    90968031   83  Linux

---

### Post by gohanssjn on 2008-02-25
I ran mkfs.ext3 -L Ubuntu /dev/sda1

It still says 1.54gb used.  Is that just normal?

---

### Post by bodhi.zazen on 2008-02-25
How big is the partition ?

---

### Post by gohanssjn on 2008-02-25
86gb

---

### Post by bodhi.zazen on 2008-02-25
Mount the partition and see what is in it. My guess is that you are looking at the file system itself (the journal takes up some space).

---

### Post by gohanssjn on 2008-02-25
Ah, ok.  It only has a Lost+Found folder.  I'll try my restore now.  Thanks!

---

