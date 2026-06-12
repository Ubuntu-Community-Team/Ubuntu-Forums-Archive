---
title: "changing partition permissions"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by gwatts on 2007-11-10
Ubuntu 7.10
My second partition on a 40 GB HD (/dev/sda)  is “/dev/sda6”. 

In Computer it is  “17.1 GB Volume :disk”.

It is in /media/disk”.

It is also in /dev/disk” where it has different folders than those in /media/disk.”

I have not been able to get chown or chmod to work - at the least because I don't know how to designate this partition is terminal nor am I able to find it in order to use  ls-l.

I don't understand why different locations and different contents.

In all three locations It is owned by root and I cannot write to it. 

How can I change permissions of this extra partition?

Any assistance will be appreciated.

Thank you.

---

### Post by Happy_Man on 2007-11-10
Have you tried ```
sudo chown 1000 /media/disk
```?

---

### Post by niteshifter on 2007-11-10
It sounds like there is no filesystem assigned to that partition. Let's try this:

Open a Terminal (Applications -> Accessories -> Terminal)
Type the below: (That is a lower-case L   NOT the digit 1 after the dash!)

```
sudo fdisk -l /dev/sda
```

Copy the output (drag your mouse over it and use Edit -> Copy in Terminal's menu) and post it here. 

(alternative to copy and paste:
```
sudo fdisk -l /dev/sda > partition-info.txt
```
then attach the file partition-info.txt to your post)

---

### Post by gwatts on 2007-11-10
Thank you.Wow!  What a rapid response!

sudo chown 1000 /media/disk  > no help -- still owned by root.


kk@jjj:~$ sudo chown 1000 /media/disk
[sudo] password for kk:
kk@jjj:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
/dev/sda6            2433        4660    17896347   83  Linux

Partition table entries are not in disk order
kk@jjj:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
/dev/sda6            2433        4660    17896347   83  Linux

Partition table entries are not in disk order
kk@jjj:~$ sudo fdisk -l /dev/sda > partition-info.txt
kk@jjj:~$ 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
/dev/sda6            2433        4660    17896347   83  Linux

Partition table entries are not in disk order

---

### Post by Happy_Man on 2007-11-10
"sudo fdisk -l" doesn't actually do anything except list partitions. the "> partition-info.txt" is just telling the computer to put the output into a file called "partition-info.txt" in your home directory. From what I can see, though, the filesystem is being picked up.

---

### Post by gwatts on 2007-11-10
Chown  must have worked. disk in media is now mine while In Computer “17.1 GB Volume :disk”. and remains owned by root

Why the difference?

Thank you both.

---

### Post by louieb on 2007-11-10
Lets try this. post the output of the **mount** command. And make sure of where the partition is mounted.

---

### Post by gwatts on 2007-11-11
kk@jjj:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

kk@jjj:~$ mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab
kk@jjj:~$ sudo fdisk -l /dev/sda
[sudo] password for kk:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
/dev/sda6            2433        4660    17896347   83  Linux

Partition table entries are not in disk order
kk@jjj:~$ mount /dev/sda6
mount: according to mtab, /dev/sda6 is already mounted on /media/disk
mount failed
kk@jjj:~$

---

### Post by louieb on 2007-11-11
Weird.  mount does not list the partition a being mounted.  
Have to think on this for a while. In the meantime have a look at [psychocats mount Linux]("http://www.psychocats.net/ubuntu/mountlinux") page. Its all I know about  it anyway.
Good Luck.

---

