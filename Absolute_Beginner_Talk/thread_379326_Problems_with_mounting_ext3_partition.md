---
title: "Problems with mounting ext3 partition"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-03-08
I have created partition with gparted.
I format it in ext3 file system.

In root terminal I write:

mount /dev/hda5 /media/hda5 -t ext3

No errors occured.

The drive I've mounted is not visible in File Browser...

What to do?

---

### Post by taurus on 2007-03-08
It's in /media/hda5 so what's the output of this command from a terminal?

```
ls -la /media/hda5
```

---

### Post by baysl on 2007-03-08
This is output:

root@linux:~# ls -la /media/hda5
total 24
drwxr-xr-x  3 root root  4096 2007-03-08 15:43 .
drwxr-xr-x 10 root root  4096 2007-03-08 16:31 ..
drwx------  2 root root 16384 2007-03-08 15:43 lost+found

---

### Post by taurus on 2007-03-08
Well, there you have it.

---

### Post by baysl on 2007-03-08
No icon is made in My computer.

And when I goto folder media/hda5 i cant write on it...

---

### Post by taurus on 2007-03-08
You can't write to it because root owns it.  You just have to change the owner to your login name and you can write to it then.  _Assuming_ your login name is **baysl**, do

```
sudo chown -R **baysl**:**baysl** /media/hdb5
ls -la /media
```

---

### Post by baysl on 2007-03-08
Ok, the disk is now writable :D

One more problem:

When I open file browser I can't see icon on the left side for hda5,
All other disks are there.

What do i do so the icon will appear there?

---

