---
title: "[SOLVED] Usb key-Read Only mount :("
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by sad_iq on 2007-07-22
Ok...Here's the deal...I have a 2 GB usb key...witch used to work fine(a few weeks ago).Then a friend took it and now that I have it, it only mounts as read only.
 I have looked trough these forums and I think that the problem seems to be a corrupted filesystem...solution...check the disk using Windows, witch I don't have..neither do my friends(I have converted them to linux). The disk mounts as user:me group:root ...I'm unable to change any permission, delete or add anything to it...basically it's useless!!!
 Tried using gparted to format it...no luck!!
 Any way I can make it mount rw??? Here is what dmesg prints:
 ```
FAT: Filesystem panic (dev sdb1)
fat_get_cluster: invalid cluster chain (i_pos 0)
File system has been set read-only
```

---

### Post by wolfen69 on 2007-07-22
if you could find a windows machine, temporarily take off data from the drive, reformat it, and replace data.

---

### Post by sad_iq on 2007-07-22
That's the deal...finding a Windows machine will be nearly impossible...I would have done it allready. So anything that doesn't involve Windows would be nice. Also **dosfsck** doesn't do anything on it :(
 I'll try looking for more solutions!

---

### Post by sad_iq on 2007-07-22
Hmmm...nothing...this will cause some severe brain-damage :( Could I format or check the disk with dosemu or something??

---

### Post by sad_iq on 2007-07-23
Anyone???

---

### Post by Lord Grover on 2007-07-23
Sorry dude, can't help, but I'm interested in the solution.

---

### Post by Mornedhel on 2007-07-23
I have had this problem as well. Sorry I can't help, since it got resolved by itself after a couple days.

---

### Post by sad_iq on 2007-07-23
Ok...solved...Finally!!! Well all I had to do is run a ```
sudo fsck -a /dev/sdb1
``` (sdb1 is my usb key) and it all worked(well all I did was that and a lot of google-ing)!!!

---

