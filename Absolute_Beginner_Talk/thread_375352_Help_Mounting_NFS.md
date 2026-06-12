---
title: "Help Mounting NFS"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-03-03
Hi,

On my Ubuntu system I have right-clicked on a directory, selected "Share Folder", chose "Share Through: NFS".  I added the IP address of my Mac (OS X Tiger) to the Allowed Hosts List: 192.168.1.100.

But when I run my mount command, I get a "Permission denied" error:

```
$ sudo mount 192.168.2.3:/home/billy/Music-1 /Users/billybob/Desktop/test
mount_nfs: can't access /home/damon/Music-1: Permission denied

```

Am I supposed to enter a username and password somewhere ?  Or should this be working ?

If I do a showmount 192.168.2.3 I get:

```
$ showmount 192.168.2.3
Hosts on 192.168.2.3:
```

And the item in my /etc/exports file is:

```
/home/billy/Music-1 *(rw)
```

And I have run a nfs-kernel-server restart (if that is even necessary).

Thanks,
Damon

---

### Post by thornomad on 2007-03-03
I searched all over the internet (like a good google-er should) and found that if I use:

```
sudo mount -o -P 192.168.2.3:/home/billybob/Music-1 /User/billy/Desktop/test
```

It works.  I am not sure what -o -P do but they make it work.

---

