---
title: "fat 32 not appearing"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-09-01
i cant acess my fat32 partition on ubuntu....

how do i mount/acess it?

---

### Post by L_o_N_e_R on 2006-09-01
bump

---

### Post by eternalis on 2006-09-01
First go to the terminal and type:
sudo fdisk -l
to find out which disk is the FAT32 drive you want to mount e.g hda3

Then type:
sudo mount /media/hda3 (replace hda3 with the drive you want to mount)

Then type:
mount
to make sure its mounted properly, thats all.

---

### Post by L_o_N_e_R on 2006-09-01
:~$ sudo mount /dev/hda4
mount: can't find /dev/hda4 in /etc/fstab or /etc/mtab



???? ok now what?

---

### Post by L_o_N_e_R on 2006-09-01
help?

---

### Post by aysiu on 2006-09-01
Read this (the whole thing):
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by L_o_N_e_R on 2006-09-01
how do i make it so it appears on my desktop?

---

### Post by aysiu on 2006-09-01
Well, if you mounted /dev/hda4 to /windows, you would do ```
ln -s /windows ~/Desktop/windows
``` Or, alternatively, you can mount it to the /media directory: /media/windows instead of /windows

---

### Post by L_o_N_e_R on 2006-09-01
ok w00t thnx man

---

