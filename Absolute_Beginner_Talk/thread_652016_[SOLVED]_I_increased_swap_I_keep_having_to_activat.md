---
title: "[SOLVED] I increased swap I keep having to activate it !!"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-28
Hi,

i increased my swap and every boot i have to activate swap on through gedit...

how can i fix this?

thanks..

---

### Post by overdrank on 2007-12-28
> **hopelessone said:**
> Hi,

i increased my swap and every boot i have to activate swap on through gedit...

how can i fix this?

thanks..


HI and you will have to add it to your fstab and then mount it. This is a good link
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Good luck!

---

### Post by hopelessone on 2007-12-28
# /dev/sda1
UUID=f0683076-a58e-4d38-af7d-8959f4072868 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b3cdf751-58b0-4d22-b19a-df738b7da172 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

this is my fstab...

the how too is a little different..as i increased it through gparted..

hope this helps...

thanks..

---

### Post by flamelab on 2007-12-28
For swap you must clear your swap line and simply write this

```
/dev/sda5 swap swap defaults 0 0
```

nothing else

and then once write on console

swapon /dev/sda5

and you have finished !

---

### Post by taurus on 2007-12-28
Is the UUID for your swap is right?  Look in /dev/disk/by-uuid to make sure they match.

```
ls -la /dev/disk/by-uuid
```

---

### Post by flamelab on 2007-12-28
&#919;e doesn't need UUIDS and all these stuff .

He has to write the simpliest line in fstab .

---

### Post by taurus on 2007-12-28
> **flamelab said:**
> &#919;e doesn't need UUIDS and all these stuff .

He has to write the simpliest line in fstab .

Excuse me for suggesting him to check his UUID then.  :roll:

p.s.  Your entry is NOT even right.

```
/dev/sda5   none   swap   sw   0   0
```

---

### Post by hopelessone on 2007-12-28
```
ls -la /dev/disk/by-uuid
```

gave me:
lrwxrwxrwx 1 root root  10 2007-12-28 16:02 10b8146a-93e8-49e2-9065-c38d3a982912 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2007-12-28 16:02 473a42db-a49f-4c20-b0dc-c26668290f74 -> ../../sdc2
lrwxrwxrwx 1 root root  10 2007-12-28 22:10 932d44e4-f827-4a06-96b2-aa68657a3a64 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-12-28 16:02 bb8ce880-6a7c-455c-ba31-9bc0a8239923 -> ../../sde1
lrwxrwxrwx 1 root root  10 2007-12-28 16:02 d68a73d0-602e-4e21-a338-f489d8c37ad3 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-12-28 16:02 f0683076-a58e-4d38-af7d-8959f4072868 -> ../../sda1

so replaced UUID=b3cdf751-58b0-4d22-b19a-df738b7da172 none swap sw 0 0 with 
UUID=932d44e4-f827-4a06-96b2-aa68657a3a64 none            swap    sw              0       0

thanks..

---

### Post by flamelab on 2007-12-28
> **taurus said:**
> Excuse me for suggesting him to check his UUID then.  :roll:

p.s.  Your entry is NOT even right.

```
/dev/sda5   none   swap   sw   0   0
```

&#921;t is VERY right . It is the same in three linux distros I've been using for years now .

Mine is in sda3 .

---

