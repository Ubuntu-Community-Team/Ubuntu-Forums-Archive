---
title: "Taking Ownership of Flash Drive"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2008-02-02
I have a flash drive that I bring back and forth to home from work.  When I put the drive in my Ubuntu machine, it says that I do not have permissions to write to it.  I tried running the  command:

```
sudo chown jason:jason /media/pocketdrive
```

but when I try this, it tells me that the drive is READ ONLY and still won't let me write to it.

The flash drive is an FAT file system because I use it mostly on my pc at work, but I need to use it at home also.  Anyone know how I can do this?  Should I add it to my FSTAB?

---

### Post by spiderbatdad on 2008-02-02
what are the permissions of media/pocketdrive? That seems to be the problem...the directory...not the flash drive.[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by jan quark on 2008-02-02
navigate to the flash directory in terminal 
and run

```
ls -l
```  ells not ones

and post the permissions displayed here please

---

### Post by kc5hwb on 2008-02-02
```
drwx------ 13 jason      root          4096 1969-12-31 18:00 POCKETDRIVE
```

I agree with you, it seems that it is the directory permissions.  However, when I try to change them, this is what I get:

```
jason@SILAS:/media$ sudo chmod ugo+rwx /media/POCKETDRIVE
[sudo] password for jason:
chmod: changing permissions of `/media/POCKETDRIVE': Read-only file system
```

And then after that the permissions look exactly the same.

---

### Post by spiderbatdad on 2008-02-02
ahh thats the fat file system. Linux cannot write to fat, as far as I know.

---

### Post by kc5hwb on 2008-02-02
Well, that is the strange thing... I have written to it before.  Sometimes when I plug it in, it lets me write to it and sometimes not.

---

### Post by spiderbatdad on 2008-02-02
maybe try chmod g+s jason /media/pocketdrive...or see if this helps.[http://www.linuxforums.org/forum/installation/296-fat32-ntfs-write-permissions.html](http://www.linuxforums.org/forum/installation/296-fat32-ntfs-write-permissions.html)
Apparently I was wrong about writing to a fat file system. You may need to set umask=000

---

### Post by kc5hwb on 2008-02-02
that command doesn't seem to work:

```
jason@SILAS:/media$ sudo chmod g+s jason /media/POCKETDRIVE
chmod: cannot access `jason': No such file or directory
```

---

### Post by jan quark on 2008-02-02
everything you ever wanted to know about mounting

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by kc5hwb on 2008-02-02
> **jan quark said:**
> everything you ever wanted to know about mounting

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

This is good information, but the USB flashdrive doesn't show up as a drive when I plug it in.  It mounts itself to a folder under /media

---

### Post by spiderbatdad on 2008-02-02
> **kc5hwb said:**
> that command doesn't seem to work:

```
jason@SILAS:/media$ sudo chmod g+s jason /media/POCKETDRIVE
chmod: cannot access `jason': No such file or directory
```
 Yeah I just took that from your previous example. The path would be the actual location of the directory /media/pocketdrive...most likely /home/jason/media/pocketdrive or /home/Desktop/media/pocketdrive.

---

