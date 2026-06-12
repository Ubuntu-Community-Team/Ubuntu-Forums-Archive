---
title: "new /home partition not recognised"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Guell on 2007-02-25
Hi, first problem I couldn't solve just by browsing the forum.

I created a separate /home-partition and copied everything onto it, then edited fstab.

Problem is that it isn't mounted as my /home, so I can't get into linux at all.

Error message: Unable to create ~/.gnome2 directory: permission denied, and some stuff about proper permissions.

When I try to mount the partition with a random name from live cd I can see the directory that's on there, but it is shown as some kind of file in stead of a folder. In the properties it says it is an unrecognised file type, and I can't open it.

I installed FSdisk in windows, and on that side I can access my new /home without any problem.

So, what to do?

---

### Post by kidders on 2007-02-26
Hi there and welcome,

Could you post some details?

[LIST]
[*]What filesystem are you using on your new /home?
[*]What changes did you make to /etc/fstab?
[*]What command did you use to perform the big copy?
[*]What is the output of **mount**?
[/LIST]
Sorry for all the questions, but we need to eliminate a few possibilities!

---

### Post by Guell on 2007-02-26
OK, thanks.

I'm on Ubuntu Edgy, my file setup is:

sda1 ntfs windows partition
sda2 ext3 contains my home folder
sda3 extended
sda5 ext3 contains ubuntu
sda6 linux-swap
sda4 fat32 with some pre-installed proprietary folders from my vendor

FSTAB:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=20c0d645-5247-469c-867a-94abb8c357fc /               ext3    defaults,erro$
# /dev/sda6
UUID=ab8d434b-6b2a-436a-bf06-92ba46ce5f26 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2       /home           ext3    nodev,nosuid    0       2


I copied the files using:

> find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

Results from mounting:
> ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /test
ubuntu@ubuntu:~$ cd /test
bash: cd: /test: Permission denied
ubuntu@ubuntu:~$ 


main thing that went wrong: during the process I cleaned up my partitions, and what I thought was an old Kubuntu-partition turned out to be my current Ubuntu. So the stuff on sda5 is actually a clean install.

Is this clear engouh?

---

### Post by kidders on 2007-02-26
> **Guell said:**
> Is this clear engouh?Yep. :-) Thanks for those details. Everything seems right. What is the result of trying "cd /test" and maybe "ls -l" using sudo?

---

### Post by Guell on 2007-02-26
That does not give much:

> ubuntu@ubuntu:~$ sudo cd /test
sudo: cd: command not found
ubuntu@ubuntu:~$ ls -l
total 0
drwxr-xr-x 2 ubuntu ubuntu 100 2007-02-26 20:23 Desktop


---

### Post by kidders on 2007-02-27
Ha! Sorry... that was a stupid thing for me to ask you to do!! What I was wondering though, is whether you have denied non-root users access to the filesystem ... I must've been asleep when I posted that method of finding out though! Are the new /home's mount point's permissions sensible?

---

### Post by Guell on 2007-03-03
I did a chmod 777 on /test, but that didn't change much. I could do a cd /test, but the folder remained empty.

Then I made a new folder,, not from my live cd, but straight in terminal mode at start-up on my actual install. I mounted my partition, performed chmod, and it worked!

I still get an error message at start-up, saying that my home .dmrc file does not have the right permissions,  but then everything starts fine, with my home right where it should be as default...

So thanks, kidders! (Go raibh mile maith agat, if I remember correctly)

---

