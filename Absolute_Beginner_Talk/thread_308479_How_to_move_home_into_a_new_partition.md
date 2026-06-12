---
title: "How to move /home into a new partition"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-28
How to move /home from a partition (i donno where is the /home located) into a partition /dev/sdb6. I have Gparted.

---

### Post by rejser on 2006-11-28
Do you have /home on the same partition as / perhaps?
I assume that you wan't to include all the data in your /home?

you can find where your home is in your fstab
"cat /etc/fstab"

---

### Post by bollix47 on 2006-11-28
See if anything [_here_]("http://www.psychocats.net/ubuntu/separatehome") helps.

---

### Post by Kurt` on 2006-11-28
You can type:

```
mount
```
by itself to see all your mounted devices, mountpoints, and their mounting parameters.

(I recommend backup up your /home partition before continuing)

To unmount /home, simply type:

```
umount /home
```
To mount it on /dev/sdb6,

```
mount -t auto /dev/sdb6 /home
```

After that, you will probably want to edit /etc/fstab (as this file controls which partitions/volumes get mounted where).

---

### Post by oliviacond on 2006-11-28
how to edit /etc/fstab after mounting it?

---

### Post by oliviacond on 2006-11-28
> **bollix47 said:**
> See if anything [_here_]("http://www.psychocats.net/ubuntu/separatehome") helps.

But I have already installed Ubuntu with a /home partition. The website says "This guide is for creating a separate /home partition if you already installed Ubuntu without a /home partition". So, can I use the guide? And the 2nd HDD has two name , /dev/hdd6 and /dev/sdb6 . So, which one should I use to mount? I have already installed Edgy, can I use Dapper Live CD?

---

### Post by bodhi.zazen on 2006-11-28
> **oliviacond said:**
> But I have already installed Ubuntu with a /home partition. The website says "This guide is for creating a separate /home partition if you already installed Ubuntu without a /home partition". So, can I use the guide? And the 2nd HDD has two name , /dev/hdd6 and /dev/sdb6 . So, which one should I use to mount? I have already installed Edgy, can I use Dapper Live CD?

If I understand you want to move your /home partition.

IMO the easiest is [Gparted Live CD](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Aletrnatly try this: [Move /Home](http://www.pclinuxonline.com/wiki/MoveEntireDirectory)

---

### Post by oliviacond on 2006-11-28
> **bollix47 said:**
> See if anything [_here_]("http://www.psychocats.net/ubuntu/separatehome") helps.

I have tried it. And the next reboot,when I want to login, it said "/home/*user* is not found." This is a disaster for me. Now I'm using the Live CD for solving this problem. Anybody pls help me!!!!!!!!!!!!!!!

---

### Post by dwblas on 2006-11-28
If you didn't edit /etc/fstab then /home was not mounted.  Try to mount /dev/sdb6 /home.  If that works then you have to remember to edit /etc/fstab so it mounts when you boot next time.

---

### Post by oliviacond on 2006-11-28
> **bollix47 said:**
> See if anything [_here_]("http://www.psychocats.net/ubuntu/separatehome") helps.

Somebody pls tell the editor to add **[SIZE="7"]sudo[/SIZE]** to the line:
> find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

---

### Post by oliviacond on 2006-11-28
> I have tried it. And the next reboot,when I want to login, it said "/home/user is not found." This is a disaster for me. Now I'm using the Live CD for solving this problem. Anybody pls help me!!!!!!!!!!!!!!!

I know what cause this. It's because I add a new line at the beginning of the /etc/fstab not the end of the line. LOL...........

---

