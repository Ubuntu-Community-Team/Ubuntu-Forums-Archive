---
title: "/boot too small?!?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Xamindar on 2007-03-25
I just installed ubuntu on my system.  In order to not have to reinstall windows as well I just used my same partition scheme that I used when I was using gentoo.  Now I am trying to do an update but it stops with telling me to free up space on /boot.  /boot is 40mb which is plenty for a few kernels and a couple of initrd and grub.  I have never even gotten near to filling it up before.  What is wrong here?  Do I have to repartition my whole hard drive for ubuntu?

---

### Post by taurus on 2007-03-25
Run this command from a terminal.

```
du -h /boot
```

---

### Post by Xamindar on 2007-03-25
```

xamindar@white-rabbit:~$ du -h /boot
12K     /boot/lost+found
167K    /boot/grub
9.7M    /boot

```
There is plenty of space.
```

/dev/sda2              37M  9.7M   26M  28% /boot

```

---

### Post by taurus on 2007-03-25
What command did you run and what exactly was the  error message?

Post those one here then.

```
df -h
```

---

### Post by Xamindar on 2007-03-25
When I run the update manager it gives me this error.  Something like this:

"The upgrade aborts now.  Please free at least 15.6M of disk space on /boot."

This is when it tries to do a "partial upgrade".

---

### Post by kaihsu on 2007-04-04
I got the same kind of trouble whilst running
update-manager -d
following instructions at
[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)
There is plenty of space on the partition.

---

### Post by kaihsu on 2007-04-10
I am trying it again today. This problem seems to have been fixed. Now the update seems to have gone further past beyond the point of previous error, and is now "Fetching and installing the upgrades". Fingers crossed!

---

