---
title: "grub not loading"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by piperwichmon on 2007-02-12
after I installed ubuntu on my second hdd (40gb), it tells me to restart without the disk, so I restart and take the disk out, but all I get is a flashing _.  so, I restart and I get 

"grub 1.5 loading.  please wait..
error 21..."

how can I fix this?

---

### Post by seshomaru samma on 2007-02-12
error 21 usually means grub cannot find the right disk
you might need to use the live Cd or a Knoppix Cd to reinstall Grub
open a terminal and write:
```
grub
```
then
```
find /boot/grub/stage1
```
replace the question marks in the following command with the output of the last command:
```
root (hd?,?)
```
then
```
setup (hd0)
```
and
```
quit
```
if this doesn't work use the LiveCd (or better yet Knoppix) and post the output of this command:
```
sudo fdisk -l 
```
(it's an L at the end not number 1)
and ```

cat /boot/grub/menu.list
```

---

