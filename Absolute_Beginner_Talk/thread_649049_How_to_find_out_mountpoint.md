---
title: "How to find out mountpoint ?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Bandicoot on 2007-12-24
I feel a bit silly asking this but how can I find out what the mountpoint is of my dvd burner ( eg hda, hdc etc) I am having problems with burning ( very slow) and I read a solution in this forum but it required the mount point of my burner , I don't know how to figure out what the mountpoint is.

---

### Post by taurus on 2007-12-24
You mean device.  Look in /etc/fstab.

```
cat /etc/fstab
```
Otherwise, look at the /var/log/messages.

```
sudo cat /var/log/messages
```

---

### Post by nick_h on 2007-12-24
Have a look in your /etc/fstab file.
From a terminal type:
```
cat /etc/fstab
```
It should have an entry for something like /dev/scd0 which will also contain the mount point.

---

### Post by bobbocanfly on 2007-12-24
The command 'df' tells you the mount points of all mounted devices and some other interesting stuff.

```
df -h
```

(-h Flag makes things easier to read)

---

### Post by taurus on 2007-12-24
> **bobbocanfly said:**
> The command 'df' tells you the mount points of all mounted devices and some other interesting stuff.

```
df -h
```

(-h Flag makes things easier to read)

It displays only mounted devices.

---

### Post by dnvikram on 2007-12-24
You can use the,"mount" command to see all the currently mounted filesystems and the mount points.

df -H command will show you the free disk space in the currently mounted filesystems and the devices on which it is mounted and it will show you in gb.

---

