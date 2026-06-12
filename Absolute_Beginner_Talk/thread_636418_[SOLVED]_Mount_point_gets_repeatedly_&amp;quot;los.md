---
title: "[SOLVED] Mount point gets repeatedly &amp;quot;lost&amp;quot;?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-09
Dazed & confused I am.

A new hard drive (bare metal), became the "main" disk. (pri/mstr). The former "boot disk" was "cloned" over to the bigger, newer drive.

For several days all was well. Then one cold-boot morning the desktop changed, losing Google's Earth & Picassa.

I ran to the forums, seeking wisdom. One klutzy reply and then I got lucky:

[http://ubuntuforums.org/showthread.php?t=633636](http://ubuntuforums.org/showthread.php?t=633636)

So, I followed the instructions in that post:

sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1

and Low! and Behold! (things went back to normal). OK OK OK several days go by and WTF? The disk has "unmounted" itself again, without warning. So I

cd /media/sda1

and the sda1 is there, next I "argued" the mount command, above and checking GParted shows it's mounted again. 

But how long can this last? Can someone tell me:

1 -- What is wrong

2 -- How to permanently solve this problem

thnx, community

---

### Post by taurus on 2007-12-09
It will last until the next time you reboot.  Then, you have to mount it by hand again.  Otherwise, add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.

---

### Post by red_Marvin on 2007-12-09
It might be good to add that some external drives have a power down mode, which you might need to get it out of manually. I have to physically power cycle mine between mounts.

Edit, VVVV Sorry, I somehow read it as you wanted to connect an external drive.

---

### Post by Mark_in_Hollywood on 2007-12-09
> **taurus said:**
> It will last until the next time you reboot.  Then, you have to mount it by hand again.  Otherwise, add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.

Will this work:


[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

?

for what it's worth:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a70ca0f-767b-4efb-8d00-7b5c800098d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=89e97a5c-4907-46f4-80eb-376f871c1d49 none            swap    sw              0       0

---

### Post by Mark_in_Hollywood on 2007-12-09
> **red_Marvin said:**
> It might be good to add that some external drives have a power down mode, which you might need to get it out of manually. I have to physically power cycle mine between mounts.

This is an internal drive. You have lost me.

---

### Post by taurus on 2007-12-09
Why don't you edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
Save it and reboot.  Now, your /dev/sda1 will be mounted to /media/sda1 each time you boot Ubuntu.

---

