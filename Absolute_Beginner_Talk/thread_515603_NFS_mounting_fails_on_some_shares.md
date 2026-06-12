---
title: "NFS mounting fails on some shares"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Eddy Dean on 2007-08-02
Ello!

I have two computers, and all the data is on computer 1 (let's call him links). Because I also want to access the files on this computer on computer 2 (rechts), I set up a NFS server on links. Most of the data is in /home/gezin/somedir. These directories all mount well on rechts. I also want to share /media/ntfs, which is a ntfs harddisk which is mounted with ntfs-3g. This however doesn't work. When I try to mount it on rechts it gives me a permission denied.

My /etc/exports of the server looks like this:
```
/home/gezin/Diversen 10.0.0.5(rw) 
/home/gezin/Films 10.0.0.5(rw) 
/home/gezin/Muziek 10.0.0.5(rw) 
/home/gezin/Office 10.0.0.5(rw) 
/media/ntfs/Fotos 10.0.0.5(rw) 
/media/ntfs/Fotos_origineel 10.0.0.5(rw) 

```

The /media/ntfs/Fotos and /media/ntfs/Fotos_origineel also have a symlink in /home/gezin.

I am certain that the problem is not in /etc/fstab on rechts, the first 4 shares work great (30MB/sec, read and write :) )

The permissions of /media/ntfs are like this:
```
drwxrwxrwx 1 root root 8192 2007-07-31 19:35 ntfs
```
and the shares:
```
drwxrwxrwx 1 root root       4096 2007-07-31 19:24 Fotos
drwxrwxrwx 1 root root      40960 2007-07-31 19:35 Fotos_origineel
```

The shares in /home/gezin/ are like this:
```
drwxr-xr-x  2 gezin gezin        4096 2007-08-02 11:16 Desktop
drwxr-xr-x  5 gezin gezin        4096 2007-08-02 11:01 Diversen
drwxr-xr-x 12 gezin gezin        4096 2007-07-24 12:55 Films
```

I don't know what the cause of the problem really is. NFS runs as a kernel module, which should mean that it is able to read and write to dirs owned by root. (right?)

Thanks in advance,
Eddy

---

### Post by TBerben on 2007-08-04
Could you please post your /etc/hosts.allow and /etc/hosts.deny files. And have a look [here](http://nfs.sourceforge.net/nfs-howto/ar01s07.html#pemission_issues), the howto saved my life many times ;)

---

