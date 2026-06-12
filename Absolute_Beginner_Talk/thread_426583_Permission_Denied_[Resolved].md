---
title: "Permission Denied [Resolved]"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by TeamMicron on 2007-04-28
I typed chmod 666 /usr and everything went haywire.  I no longer have permission to do anything.  How do I change this?  Thank you for the help.

---

### Post by [S|G] on 2007-04-28
Try this:
```
sudo chmod 755 /usr
```

If you can't use sudo, try rebooting, going to recovery mode and typing this from there

---

### Post by aysiu on 2007-04-28
I think it's supposed to be 751 in /usr

After you've fixed that, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by [S|G] on 2007-04-28
> **aysiu said:**
> I think it's supposed to be 751 in /usr
I think it's 755 (rwxr-xr-x), else he wouldn't be able to read the files, right?

---

### Post by aysiu on 2007-04-28
I got this, though: ```
username@ubuntu:~$ cd /usr
username@ubuntu:/usr$ ls -l
total 120
drwxr-xr-x   2 root root 36864 2007-04-28 18:33 bin
drwxr-xr-x   2 root root  4096 2007-04-23 19:49 games
drwxr-xr-x   9 root root  4096 2007-04-26 23:29 include
drwxr-xr-x 136 root root 49152 2007-04-28 18:33 lib
drwxr-xr-x  10 root root  4096 2007-04-08 23:11 local
drwxr-xr-x   2 root root  8192 2007-04-28 18:28 sbin
drwxr-xr-x 242 root root  8192 2007-04-28 18:33 share
drwxrwsr-x   5 root src   4096 2007-04-26 19:26 src
drwxr-xr-x   3 root root  4096 2007-01-21 11:00 X11R6
``` Isn't that 751?

---

### Post by [S|G] on 2007-04-28
> **aysiu said:**
>  Isn't that 751?
751 = rwxr-x--x
755 = rwxr-xr-x

Also, you're looking at the contents of your /usr. Luckly he didn't make a recursive chmod, so he only changed his /usr. If you take a look:

```

diegolima@ColdWire:/$ cd /
diegolima@ColdWire:/$ ls -l
drwxr-xr-x  11 root root  4096 2007-04-19 07:56 usr

```

So the /usr directory is actually 755 :)

---

### Post by TeamMicron on 2007-04-29
Thanks a lot guys. solved it!

---

