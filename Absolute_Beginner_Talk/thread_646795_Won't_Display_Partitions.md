---
title: "Won't Display Partitions"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Tubob on 2007-12-21
I'm new to Ubuntu and currently dual booting Gutsy and Vista Home Premium. 

It worked previously as it should but just today I have lost the ability to access my Vista partition. This is the partition containing all of my media and program files and such and I need it. 

What is going on here?

---

### Post by LaRoza on 2007-12-21
I assume Vista is bootable (the partition is still there)

Post the output of:

```

cat /etc/fstab

```

---

### Post by taurus on 2007-12-21
I bet you didn't shutdown your vista cleanly so Ubuntu won't mount it from /etc/fstab unless you use the force option!  What happens if you try to mount it from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs **/dev/sda1** /media/windows
```
_Assuming_ **/dev/sda1** is your windows partition.

---

### Post by Tubob on 2007-12-21
Yeah, Vista works and I entered that. It appears to have worked but how do I refresh my desktop and stuff so it shows up in Places and on the desktop?

---

### Post by Tubob on 2007-12-21
It told me that that directory already exists but it's still not being displayed.

Any other ideas?

---

### Post by taurus on 2007-12-21
What do you mean by display?  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

