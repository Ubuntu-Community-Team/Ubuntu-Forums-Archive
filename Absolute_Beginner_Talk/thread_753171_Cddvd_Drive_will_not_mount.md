---
title: "Cd/dvd Drive will not mount"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by MantinoX on 2008-04-12
Ive have looked on the forums and i still cant seem to find the answer:

When trying to load a cd or even mount i get the message 
                         
"Mount: Special device dev/hdd does not exist....

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7168014b-0b81-475c-9c9b-30bc9d5aafa9 /               ext3    defaults,erro$
# /dev/sda5
UUID=216a3322-ebdc-4e94-a216-81400e15151a none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
 
```

I have also set my bios so that the cd rom drive was not set to boot.

So what am i doing wrong?


thanks

---

### Post by Inxsible on 2008-04-12
Ideally CD drives should automount when you insert any CD/DVD in it. Try to comment the line for the cd/dvd in the fstab and then try inserting any CD or DVD.

see if that works. I for one, don't have an entry for my cd drive in fstab

---

### Post by MantinoX on 2008-04-12
"Try to comment the line for the cd/dvd in the fstab "

What do you mean by this?


Thanks

---

### Post by Inxsible on 2008-04-12
> **MantinoX said:**
> "Try to comment the line for the cd/dvd in the fstab "

What do you mean by this?


ThanksIn the fstab that you posted, put a # sign before the /dev/hdd line (which points to your cd drive)

---

### Post by MantinoX on 2008-04-12
K after the add of # I now do not have a cd rom drive recgonized after a system restart.:(

---

### Post by Inxsible on 2008-04-12
> **MantinoX said:**
> K after the add of # I now do not have a cd rom drive recgonized after a system restart.:(And you do have a CD/DVD in the drive correct ?

---

### Post by MantinoX on 2008-04-12
I do, what are other possibilities that could be involved?

---

### Post by Inxsible on 2008-04-12
> **MantinoX said:**
> I do, what are other possibilities that could be involved?
could you post the output of ```
 ls -l /dev | grep hd
```
and ```
ls -l /dev | grep sd
```

---

### Post by MantinoX on 2008-04-12
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7168014b-0b81-475c-9c9b-30bc9d5aafa9 /               ext3    defaults,erro$
# /dev/sda5
UUID=216a3322-ebdc-4e94-a216-81400e15151a none            swap    sw           $
# /dev/hdd      /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



```

---

### Post by MantinoX on 2008-04-12
```
mantino@mantino-desktop:~$  ls -l /dev | grep hd
brw-rw---- 1 root   disk      3,   0 2008-04-12 12:29 hda
brw-rw---- 1 root   disk      3,   1 2008-04-12 12:29 hda1
brw-rw---- 1 root   disk      3,  64 2008-04-12 12:29 hdb
brw-rw---- 1 root   disk      3,  65 2008-04-12 12:29 hdb1
mantino@mantino-desktop:~$ ls -l /dev | grep sd
crw-rw-rw- 1 root   tty       2,  61 2008-04-12 12:29 ptysd
brw-rw---- 1 root   disk      8,   0 2008-04-12 12:29 sda
brw-rw---- 1 root   disk      8,   1 2008-04-12 12:29 sda1
brw-rw---- 1 root   disk      8,   2 2008-04-12 12:29 sda2
brw-rw---- 1 root   disk      8,   5 2008-04-12 12:29 sda5
brw-rw---- 1 root   disk      8,  16 2008-04-12 12:29 sdb
brw-rw---- 1 root   disk      8,  17 2008-04-12 12:29 sdb1
crw-rw-rw- 1 root   tty       3,  61 2008-04-12 12:29 ttysd
mantino@mantino-desktop:~$ 


```

---

### Post by Inxsible on 2008-04-12
> **MantinoX said:**
> ```
mantino@mantino-desktop:~$  ls -l /dev | grep hd
brw-rw---- 1 root   disk      3,   0 2008-04-12 12:29 hda
brw-rw---- 1 root   disk      3,   1 2008-04-12 12:29 hda1
brw-rw---- 1 root   disk      3,  64 2008-04-12 12:29 hdb
brw-rw---- 1 root   disk      3,  65 2008-04-12 12:29 hdb1
mantino@mantino-desktop:~$ ls -l /dev | grep sd
crw-rw-rw- 1 root   tty       2,  61 2008-04-12 12:29 ptysd
brw-rw---- 1 root   disk      8,   0 2008-04-12 12:29 sda
brw-rw---- 1 root   disk      8,   1 2008-04-12 12:29 sda1
brw-rw---- 1 root   disk      8,   2 2008-04-12 12:29 sda2
brw-rw---- 1 root   disk      8,   5 2008-04-12 12:29 sda5
brw-rw---- 1 root   disk      8,  16 2008-04-12 12:29 sdb
brw-rw---- 1 root   disk      8,  17 2008-04-12 12:29 sdb1
crw-rw-rw- 1 root   tty       3,  61 2008-04-12 12:29 ttysd
mantino@mantino-desktop:~$ 


```I see the problem now, In your fstab you are pointing to /dev/hdd whereas you do NOT have a hdd, your cd drive is probably named hcd or scd. could you run this and get the output please```
ls -l /dev | grep sc
``` or ```
ls -l /dev | grep hc
```

---

### Post by MantinoX on 2008-04-12
```
mantino@mantino-desktop:~$ ls -l /dev | grep sc
crw-rw---- 1 lp     scanner  99,   0 2008-04-12 12:29 parport0
crw-rw-rw- 1 root   tty       2,  60 2008-04-12 12:29 ptysc
crw-rw-rw- 1 root   tty       3,  60 2008-04-12 12:29 ttysc

```

the other one dosen't work.

---

### Post by Inxsible on 2008-04-12
> **MantinoX said:**
> ```
mantino@mantino-desktop:~$ ls -l /dev | grep sc
crw-rw---- 1 lp     scanner  99,   0 2008-04-12 12:29 parport0
crw-rw-rw- 1 root   tty       2,  60 2008-04-12 12:29 ptysc
crw-rw-rw- 1 root   tty       3,  60 2008-04-12 12:29 ttysc

```the other one dosen't work.
That's weird, because its not recognizing the drive at all. This is my output of the same command```
lrwxrwxrwx 1 root   root           4 2008-04-12 09:35 cdrom -> scd0
lrwxrwxrwx 1 root   root           4 2008-04-12 09:35 cdrw -> scd0
lrwxrwxrwx 1 root   root           4 2008-04-12 09:35 dvd -> scd0
lrwxrwxrwx 1 root   root           4 2008-04-12 09:35 dvdrw -> scd0
crw-rw-rw- 1 root   tty       2,  60 2008-04-12 05:35 ptysc
brw-rw---- 1 root   cdrom    11,   0 2008-04-12 05:35 scd0
lrwxrwxrwx 1 root   root           4 2008-04-12 09:35 sr0 -> scd0
crw-rw-rw- 1 root   tty       3,  60 2008-04-12 05:35 ttysc

```

---

### Post by MantinoX on 2008-04-12
Solved the problem the cdrom drive had a loose connection (ide cable) but im Glad we went over over the disk setup. I find it awkward that is was the cable though.


Thank you for your time :)

---

### Post by Inxsible on 2008-04-12
> **MantinoX said:**
> Solved the problem the cdrom drive had a loose connection (ide cable) but im Glad we went over over the disk setup. I find it awkward that is was the cable though.


Thank you for your time :)Aha !!! Well I am glad you worked it out. Could you mark the thread solved.

---

