---
title: "How to get to 2nd HDD"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-07-01
I just put a new 80HDD in my pc and made it the primary HDD and reinstalled Ubuntu on it. But now how do I get to my old HDD on Ubuntu it's the slave to the other 1.

---

### Post by 505 on 2007-07-01
It is mounted somewhere. Open a terminal and type 'mount' You should see an entry for '/dev/mapper/hdb1' somewhere. and behind that the path where it is mounted. You can change this mount point by editing /etc/fstab
If it is nowehere, you should mount it yourself to a directory of your choice.

---

### Post by microsoft92sucks on 2007-07-02
> **505 said:**
> It is mounted somewhere. Open a terminal and type 'mount' You should see an entry for '/dev/mapper/hdb1' somewhere. and behind that the path where it is mounted. You can change this mount point by editing /etc/fstab
If it is nowehere, you should mount it yourself to a directory of your choice.
```

spaje@EggHead:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```
why is it saying somthing about an error?
And I can't get to it some more help please.

---

### Post by Nythain on 2007-07-02
create a place to mount the old hard drive
```

sudo mkdir /media/other_drive

```
for instance... it can be any folder anywhere, just make sure you make the folder.
then open up your fstab
```

gksudo gedit /etc/fstab

```
add a line thats something like this
```

/dev/sdwhateveryourseconddrivepartitionis    /media/whateverfolderyoumade   filesystem(examples ext3, ext2, vfat, ntfs)   defaults   0    2

```
i hope you can make sense out of that... then mount it
```

mount -a

```

i really hope i didnt confuse you at all with that... but theoretically it should work out ok

---

### Post by microsoft92sucks on 2007-07-02
I got it all working thanks for the help.

---

