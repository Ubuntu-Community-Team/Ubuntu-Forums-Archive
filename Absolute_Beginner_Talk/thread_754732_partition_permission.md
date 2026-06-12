---
title: "partition permission"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by boriska42 on 2008-04-14
hey....
I have just recently left the evil clutches of windows...and have switched to ubuntu...and I am loving every minute of it...however,  I have a small problem..

..I just created a new partition, using gnome partition editor....it mounted fine, but for some reason, only made
read-only access...how can I change it, so that I have read and write privileges.for that partition...thank you very much.....

---

### Post by hyper_ch on 2008-04-14
If it's an additional partition for data and stuff, do the following. If it's a partition containing required system files, don't do that!

```

sudo chown -R USER.USER /path/to/mountpoint
sudo chmod -R 0755 /path/to/mountpoint

```

And of course replace USER and /path/to/mountpoint with the actual values of your username and where you have it mounted...

---

### Post by ibutho on 2008-04-14
Post the contents of your /etc/fstab. Do you the device name that was given to your partition (e.g. /dev/sda1).

---

### Post by Trail on 2008-04-14
You might try right-clicking on it, and check the permissions tab. Check who the owner of the partition is. From the sound of it, either the owner is root, or it's set to read-only permissions.

If the owner is root, which is probably it, you can open a terminal and type
```

sudo chown `whoami`:`whoami` /media/PARTITION_LABEL

```
Quotes here are important to be exactly like that, so copy-paste it. And of course, you substitute PARTITION_LABEL with the correct name (for example, it could be /media/sdb1.)

Edit: Too slow. Equivalent to what hyper_ch said.

---

### Post by SnakeHips on 2008-04-14
and here's a really useful guide...

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by njparton on 2008-04-14
It's probably mounted as read-only (ro) in your fstab file.

---

### Post by boriska42 on 2008-04-14
Thank you very much everybody for the quick reply...everything works beautifully...thanks again.

---

