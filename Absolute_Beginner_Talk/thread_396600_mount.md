---
title: "mount"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-29
hi there

 Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         500     4016218+  83  Linux
/dev/hdc2            9649        9729      650632+   5  Extended
/dev/hdc3             501        5059    36620167+  83  Linux
/dev/hdc4            5060        9648    36861142+  83  Linux
/dev/hdc5            9649        9729      650601   82  Linux swap / Solaris


i want to mount the hdc3, and hdc4 to be 2 partitions so how can i do that ???

, by the way is there is any way to obtain an icon like my computer in windows ??

---

### Post by mikewhatever on 2007-03-29
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

About the desktop icon, anything mounted in /media will have it, so choose your mount points as /media/hdc3 and /media/hdc4.

---

### Post by ceezax on 2007-03-29
i did what you told in the page but i don't got anything

secondly , what is the difference between running commands in sudo , and turning to root user using su command then performing the tasks ??

what is the difference between sudo , su ??

what is the command associated with deleting ??

---

### Post by Bachstelze on 2007-03-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-03-29
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hdc3   /media/hdc3   ext3   defaults   0   1
/dev/hdc4   /media/hdc4   ext3   defaults   0   1
```
Save it.  Then, create two mount points and mount them.

```
sudo mkdir /media/hdc3 /media/hdc4
sudo mount -a
df -h
```

---

