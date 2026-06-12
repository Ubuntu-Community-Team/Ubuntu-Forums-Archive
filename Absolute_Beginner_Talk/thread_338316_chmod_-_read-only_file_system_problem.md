---
title: "chmod - read-only file system problem"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by chrismacp on 2007-01-14
Hello,

I have just installed the ubuntu 6.10 Lamp server using the appropriate option from the CD. 

I am also going through the setup tutorial found here [http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p6]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p6")

The problem is occurring when I try ```
vi /etc/mime.types 
```. It only opens this file up as read only. 

So I try and chmod the file, using ```
chmod 751 /etc/mime.types
``` but I get the following message:

```
chmod: changing permissions of '/etc/mime.types': Read-only file system
```

I still cant write to the file and I'm not sure what to do next. I am very new to Linux and so would be grateful for any advice.

Also, how do you find out current permissions of a file/dir?

---

### Post by taurus on 2007-01-14
```
sudo vi /etc/mime.types
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2007-01-14
for current permissions use the -l flag:

ls -l

or 

ls -l | grep mime.types

To change permissions, use sudo

```
sudo chmod 751 /etc/mime.types
```

You may also need sudo with vi:

```
sudo vi /etc/mime.types
```

---

### Post by chrismacp on 2007-01-14
Sorry, forgot to mention I had switched to root using 'su' command. 

using ls, the file seems to have these permissions -rw-r--r


> **taurus said:**
> ```
sudo vi /etc/mime.types
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-01-14
Here's my /etc/mime.types.

```
-rw-r--r-- 1 root root 20423 2006-06-15 16:13 /etc/mime.types
```
As you can see, root can modify it anytime.

---

### Post by chrismacp on 2007-01-14
Ok, so mine seems to be the same, I am just going to try and edit again. thanks for your timely responses by the way!

---

### Post by chrismacp on 2007-01-14
Still seems to be read only, I've attached a screen shot. I'm very confused now. not sure how on earth to make it writeable.

---

### Post by taurus on 2007-01-14
Instead of logging in as root, why don't you run it with the sudo command!

```
sudo vi /etc/mime.types
```

p.s.
```
ls -la /etc/mime.types
```

---

### Post by chrismacp on 2007-01-14
I have just tried it all again using sudo, not in root account. It is all still the same, and vi opens up a readonly file which I cannot edit. 

I have been using root account as it said to in the tutorial, I think because it goes through many commands and having to type password in for each one is tedious. 

I am failing to understand what's going on though. If I am logged in as root, then if I chmod something then surely it should change permissions. How else could I do it? Does doing this over SSH have any bearing on the problem at all do you think?

---

### Post by taurus on 2007-01-14
```
ls -la /etc/mime.types
```

---

### Post by chrismacp on 2007-01-14
I think you want to see the results so here's what I have just tried

```
chrismacp@dev:~$ sudo chmod 777 /etc/mime.types
chmod: changing permissions of `/etc/mime.types': Read-only file system
chrismacp@dev:~$ ls -la /etc/mime.types
-rw-r--r-- 1 root root 20423 2006-06-15 21:13 /etc/mime.types
```

---

### Post by chrismacp on 2007-01-14
Anyone have any more suggestions at all, I cant find much help in any documentation I've looked at as it seems that it should work the way I have tried it.

---

### Post by chrismacp on 2007-01-14
It appears that other files are now read only too. Maybe there is something major here that I've done wrong. 

I just tried to ```
vi /etc/network/interfaces
``` and that is also read only now, but it definitely wasn't yesterday. 

Is there some command that can make the whole file system read only? Maybe I have inadvertently entered something incorrect.

I know the 'ls' command I thought was 'is' due to the fonts on the forum, so maybe I mistook something somewhere.

---

### Post by taurus on 2007-01-14
```
ls -la /
cat /etc/fstab
```

---

### Post by Buck2348 on 2007-01-14
```
mount
```
The output from this command should give information on each file system you have mounted, including /, the root system which includes /etc.  See if the line for that file system (e.g. hdb1) has "ro" in it for read-only.  If so it would seem that it was mounted read-only, probably as a result of this item in /etc/fstab
```
errors=remount-ro
```
Try rebooting and see if that fixes it.

Buck

---

### Post by chrismacp on 2007-01-14
Thanks for the reply, but can you tell me what the cat command is? Just it just show a file?

Here is the output anyway, I cant really tell much from it. The only bit I added was the 'usrquota,grpquota' 

```

root@dev:/home/chrismacp# ls -la /
total 120
drwxr-xr-x 21 root root  4096 2007-01-14 13:18 .
drwxr-xr-x 21 root root  4096 2007-01-14 13:18 ..
drwxr-xr-x  2 root root  4096 2007-01-13 18:47 bin
drwxr-xr-x  3 root root  4096 2007-01-13 18:45 boot
lrwxrwxrwx  1 root root    11 2007-01-13 16:35 cdrom -> media/cdrom
drwxr-xr-x 12 root root 13300 2007-01-14 14:10 dev
drwxr-xr-x 60 root root  4096 2007-01-14 13:19 etc
drwxr-xr-x  4 root root  4096 2007-01-13 22:19 home
drwxr-xr-x  2 root root  4096 2007-01-13 16:37 initrd
lrwxrwxrwx  1 root root    32 2007-01-13 16:41 initrd.img -> boot/initrd.img-2.6.17-10-server
drwxr-xr-x 15 root root  4096 2007-01-13 16:52 lib
drwxr-xr-x  2 root root 49152 2007-01-13 16:34 lost+found
drwxr-xr-x  3 root root  4096 2007-01-13 16:35 media
drwxr-xr-x  2 root root  4096 2006-10-19 23:49 mnt
drwxr-xr-x  2 root root  4096 2007-01-13 16:37 opt
dr-xr-xr-x 54 root root     0 2007-01-14 14:10 proc
-rw-------  1 root root     0 2007-01-14 13:18 quota.group
-rw-------  1 root root     0 2007-01-14 13:18 quota.user
-rw-------  1 root root  1024 2007-01-13 16:47 .rnd
drwxr-xr-x  2 root root  4096 2007-01-13 17:30 root
drwxr-xr-x  2 root root  4096 2007-01-14 13:16 sbin
drwxr-xr-x  2 root root  4096 2007-01-13 16:37 srv
drwxr-xr-x 11 root root     0 2007-01-14 14:10 sys
drwxrwxrwt  4 root root  4096 2007-01-14 13:16 tmp
drwxr-xr-x 11 root root  4096 2007-01-13 16:37 usr
drwxr-xr-x 14 root root  4096 2007-01-13 16:46 var
lrwxrwxrwx  1 root root    29 2007-01-13 16:41 vmlinuz -> boot/vmlinuz-2.6.17-10-server
root@dev:/home/chrismacp# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=66a573d9-a10e-4c90-ae6a-92e61c39d705 /               ext3    defaults,errors=remount-ro,usrquota,grpquotA 0       1
# /dev/hda5
UUID=163d44d3-3e8f-4d8d-9c3e-6fb1a97aab5c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

> **taurus said:**
> ```
ls -la /
cat /etc/fstab
```

---

### Post by taurus on 2007-01-14
Boot into recovery mode from GRUB menu and remove this, "**,usrquota,grpquotA**", from the entry for your / in /etc/fstab.

```
vi /etc/fstab
```

---

