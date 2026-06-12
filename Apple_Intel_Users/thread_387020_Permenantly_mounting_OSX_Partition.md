---
title: "Permenantly mounting OSX Partition"
date: 2007-03-17
forum: Apple Intel Users
---

### Post by AnthonyJK@gmail.com on 2007-03-17
Is there a way to permantly mount the OSX partion. I can do it manually by typing:

sudo mount /dev/sda2 /mnt/macosX

in terminal but I have to do it everytime I boot up. Ive search the forum and found a post about editing my fstab to get it to mount but it didnt work for me. any help would be appreciated thanks!

---

### Post by kidders on 2007-03-17
Hi there,

Adding your filesystem to /etc/fstab is the right thing to do. Could you post the addition you made, and any error messages it produced?

---

### Post by david_edmundson on 2007-03-17
Add this to /etc/fstab
/dev/sda2       /mnt/macosX        hfsplus auto,defaults     0       0

Spacing is important in this file (a bad design imho) it should be a tab between group of words.

Change auto to noauto, if you don't want it on as soon as you boot up.

---

### Post by AnthonyJK@gmail.com on 2007-03-18
Thanks that worked :)

---

