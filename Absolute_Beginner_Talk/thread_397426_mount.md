---
title: "mount"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-30
i have this

Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         500     4016218+  83  Linux
/dev/hdc2            9649        9729      650632+   5  Extended
/dev/hdc3             501        5059    36620167+  83  Linux
/dev/hdc4            5060        9648    36861142+  83  Linux
/dev/hdc5            9649        9729      650601   82  Linux swap / Solaris



now i wanna mount hdc3,4 as partitions on the desktop , so how can i do that ??

please paste the full code , and don't point or link another page 

hint : i wanna those partitions to be readable and writable by all users

---

### Post by taurus on 2007-03-30
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
Now, you need to change the ownership of those two mount points to you, assuming your login name is **ceezax**.

```
sudo chown -R **ceezax**:**ceezax** /media/hdc3
sudo chown -R **ceezax**:**ceezax** /media/hdc4
sudo chmod -R 777 /media/hdc3 /media/hdc4
ls -la /media
```

---

### Post by ceezax on 2007-03-30
i have 2 directories on the desktop which i can't delete 

named test1,test2

please give me the command to remove those 2 directories

---

### Post by bodhi.zazen on 2007-03-30
> **ceezax said:**
> i have 2 directories on the desktop which i can't delete 

named test1,test2

please give me the command to remove those 2 directories

rm -rf ~/Desktop/test1 ~/Desktop/test2

---

### Post by ceezax on 2007-03-30
what does the ~ stand for ??

---

### Post by bodhi.zazen on 2007-03-30
~ is short hand for /home/user_name

---

