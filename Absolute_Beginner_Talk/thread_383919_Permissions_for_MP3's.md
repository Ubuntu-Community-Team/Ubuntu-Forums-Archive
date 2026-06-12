---
title: "Permissions for MP3's"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-03-13
I have my mp3's on a seperate partition, and they won't play unless they have execute permissions. 

Based on recommendations, I changed my fstab
The new fstab line is:
```
/dev/hdb7  /home/username/multimedia ext3   rw,defaults,nouser,nodev   0       1
```

The old fstab line was:
```
/dev/hdb7  /home/username/multimedia ext3    defaults,errors=remount-ro 0       1
```

and it made no difference.

According to ls -l, the mp3's and folders are all owned by me (my username) but they will only play with permissions of 777, not 666 or 444.

Tag-along question: how much of a security risk is it leaving all these files as 777?

-Andrew

---

### Post by gangrelsurf on 2007-03-13
> **Atreus12 said:**
> I have my mp3's on a seperate partition, and they won't play unless they have execute permissions. 

Based on recommendations, I changed my fstab
The new fstab line is:
```
/dev/hdb7  /home/username/multimedia ext3   rw,defaults,nouser,nodev   0       1
```

The old fstab line was:
```
/dev/hdb7  /home/username/multimedia ext3    defaults,errors=remount-ro 0       1
```

and it made no difference.

According to ls -l, the mp3's and folders are all owned by me (my username) but they will only play with permissions of 777, not 666 or 444.

Tag-along question: how much of a security risk is it leaving all these files as 777?

-Andrew

change the part of your /etc/fstab that reads:

```
/dev/hdb7  /home/username/multimedia ext3   rw,defaults,nouser,nodev   0       1
```

to be:

```
/dev/hdb7  /home/username/multimedia ext3   uid=1000,gid=1000,users,rw   0       1
```

saying 1000 is your id. Type 'id' at the command line to check

---

### Post by gangrelsurf on 2007-03-13
Tag along answer:

Big

Anyone can mess with those.

I'm not sure what to reset those mp3's to, though, 660?  I don't think that they need to be exacutable, really, unless other people on the system are supposed to have access to them, I would try them at 600

---

### Post by Atreus12 on 2007-03-14
I changed the fstab line, then umounted /dev/hdb7, then did a mount -a and got an error

```
[17182838.124000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
```

The output of the 'id' comand is:

```
username@andrew:~$ id
uid=1000(username) gid=1000(username) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(username)


```

-Andrew

---

### Post by gangrelsurf on 2007-03-14
> **gangrelsurf said:**
> change the part of your /etc/fstab that reads:

```
/dev/hdb7  /home/username/multimedia ext3   rw,defaults,nouser,nodev   0       1
```

to be:

```
/dev/hdb7  /home/username/multimedia ext3   uid=1000,gid=1000,users,rw   0       1
```

saying 1000 is your id. Type 'id' at the command line to check

Hey, sorry I took so long to get back. Turns out that uid / gid only works on vfat disks. Looking at what I put up there though, I think it's redundant anyway. The 'users' means that anyone can mount / umount. So just take the uid / gid stuff out, if you haven't already. Try it like that.

---

### Post by Atreus12 on 2007-03-14
I can mount it just fine like that, but I still have to give +x to be able to play the files.

---

### Post by gangrelsurf on 2007-03-14
alright, I'm not sure about this but try removing the +x, then adding the parameter 'exec'

---

