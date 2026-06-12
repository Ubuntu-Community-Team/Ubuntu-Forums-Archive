---
title: "EXT3 Read Only Drive"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-01-21
I have been reading left and right on how to change permissions on my drive and I haven't found an answer yet  :confused:   :confused:  ..I have two slave drives that I use to use in Windows and I want to use them both exlusively for Ubuntu now but I can't write at all on them.  They are **not** NTFS... I reformatted them with GParted to EXT3...  I think I'm missing a vital step somewhere..

In the posts I've read people keep asking people with Read/Write problems to type:
```
sudo mount
```

These are my results... I hope it helps...

```

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=chrisjmccrum)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev)
/dev/sdb5 on /media/disk-1 type ext3 (rw,nosuid,nodev)

```

---

### Post by Sand Lee on 2008-01-21
Have you already installed Ubuntu? To change permissions you have to run nautilus as root with, ```
gksudo nautilus
``` Then enter the folder containing your partitions/harddisks, right click on your mounted partition or hardisk, go to Permissions, and change Owner and Group from root to your username.

---

### Post by Aysah on 2008-01-21
yes I have...I'm running Gutsy right now...  I have seen this nautilus thing that you showed me but I dont understand it really...  sorry to bother you but do you mind explaining how I can specifically add my two SATA drives  under my permission...  when I ran "gksudo nautilus" it opened a window that just has a folder called "Desktop"   

what should I do now?

---

### Post by capink on 2008-01-21
Try running these two commands:

```
sudo chmod 666 /media/disk
```
```
sudo chmod 666 /media/disk-1
```

---

### Post by Aysah on 2008-01-21
well I guess in a sense it half worked being that when i rightcklick in the drive "/media/disk" it APPEARS to have the option to create folder now but when I actually click it the following error comes up: "Error Creating new folder... You do not have permission to write to the destination".  As for the second drive..

```
sudo chmod 666 /media/disk-1
```

```
chmod: cannot access `/media/disk-1': No such file or directory
```
is what I get...


there is really nothing at all on these drives at all...like **nothing...**  would it be easier for someone just to show me what i need to do from square one to get this working??  All i want is these drives to be is storage and the location of WINE installations.  Basically full read/write/execute access...  I dont care if everything gets wiped and reformatted... whatever is easier

---

### Post by Sand Lee on 2008-01-21
After running the command I gave, you have to navigate to /media and right-click on the folders you want to gain permission on.

---

### Post by logos34 on 2008-01-21
> **Aysah said:**
> there is really nothing at all on these drives at all...like **nothing...**  would it be easier for someone just to show me what i need to do from square one to get this working??  All i want is these drives to be is storage and the location of WINE installations.  Basically full read/write/execute access...  I dont care if everything gets wiped and reformatted... whatever is easier

read this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

remember to run chmod AND chown on new mount points

---

### Post by Aysah on 2008-01-21
I tried it and right clicked on the drives and everything under permissions is greyed out..  It says you are not the ownder, so you can't change these permissions.  I thought if you run sudo and type your password in that it makes you temporarily the owner...  I'm a little confused now..

---

### Post by Sand Lee on 2008-01-21
Did you run gksudo nautilus, and navigate to the folder before right clicking it? gksudo will make you the owner.

---

### Post by Aysah on 2008-01-21
> **logos34 said:**
> read this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

remember to run chmod AND chown on new mount points

wow thank you soo much..  all of you thanks for the quick feedback and help on this matter.  :-k It actually all collaboratively made me understand how the drives are represented in linux...

Thanks Again!! :)

---

### Post by Ux64 on 2008-01-22
I have similar problem, but hint`s didn`t help.

For some strange reason disk is fine as long as I won`t boot from it. But when I boot from it / is read only. And that really sucks.

I booted from live cd and everything works great. I also checked disk, and no help.

Now I have spent two days with this strange problem.

---

### Post by Aysah on 2008-01-23
> **Ux64 said:**
> I have similar problem, but hint`s didn`t help.

For some strange reason disk is fine as long as I won`t boot from it. But when I boot from it / is read only. And that really sucks.

I booted from live cd and everything works great. I also checked disk, and no help.

Now I have spent two days with this strange problem.

I'm far from an expert to any of this but being new to linux I have realized that alot of my problems were coming from my lack of knowledge of the 'chmod' utility and setting the proper permissions...

I actually ended up reading this article, which was quite useful...
[http://www.ss64.com/bash/chmod.html]("http://www.ss64.com/bash/chmod.html")

---

### Post by Ux64 on 2008-01-23
Yeah. And I have to admit that data corruption was caused for some other reason.

But actually the read only mounting wasn't caused by I/O errors. It was caused by modifying fstab without enough knownledge.

I changed journal=writeback to journal=data and didn't realize that I would need to do other things except change that text.

Now I changed irqpoll option for boot. Let's see if I finally get rid of corrupting data. I also do sync before shutting system down.

---

