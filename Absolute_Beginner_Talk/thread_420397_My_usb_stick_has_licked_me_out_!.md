---
title: "My usb stick has licked me out !"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Pat Hall on 2007-04-23
A friend of mine ( not sure how long they will remain so ) wanted to see my ubuntu setup as he is thinking of leaving the world of Gates , I left him alone for five minutes only to discover on my return that he managed to reformat my 1Gb usb stick to ext3 complete with its own little lost+found , and now whenever I try to reformat it back to fat16 I get the message that the operation failed because it contains a mounted volume even though I have unmounted it . I am using gParted and Feisty . Any help would be gratefully received .

---

### Post by Pat Hall on 2007-04-23
Sorry that should have read locked me out ! I am no techno perv honest !

---

### Post by MikeDX on 2007-04-23
ok heres the solution in 3 easy steps

1. open a terminal
2. sudo umount -a
3. sudo gparted

then format the stick .. i guess its /dev/sda DONT format /dev/hda! (or whatever your main drive is)

Good luck!

---

### Post by kpkeerthi on 2007-04-23
Disable automounting from System -> Preference -> Removable devices and try again.

---

### Post by Pat Hall on 2007-04-23
Thanks for the help , success !

---

