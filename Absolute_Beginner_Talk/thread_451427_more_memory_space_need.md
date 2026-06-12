---
title: "more memory space need"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by winubu on 2007-05-22
Hello My name is Kevin. I live in Holland. I am an american working here. I downloaded ubuntu edgy eft on my usb hard drive. It is working well. But , it seems I have only 3.7 gig of memory on a 250 gig drive..The partition program set it up so. Now when I want to download more software for ubuntu. I am told there is not enough space. I am a carpenter and not a computer wiz. I have windows xp pro and have always wanted to start something with linux. So far so good but I have no memory to go further with it.  What do I need to do, Please?

---

### Post by lamalex on 2007-05-22
can you past the output of ```
sudo fdisk -l
```
you might need to repartition your hd to give ubuntu more space.

---

### Post by Cypher on 2007-05-22
Open up a terminal by Applications->Accessories->Terminal and type
```

sudo fdisk -l
df -h
mount

```
and show us the output..

---

### Post by winubu on 2007-05-25
Hey, thanks for helping me out. This is the info I have.

             fdisk:  [-b ssz]  DISK                  Change partition table
             fdisk   -l  [-b ssz]  [-u]  DISK      List partion table(s)
             fdisk   -s  PARTITION                  Give partion size(s)  in blocks
             fdisk   -v                                        Give  fdisk  version
Here DISK is something like  /dev/sda
and  PARTION is something like /dev/hda7
-u: give Start and End in sector  (instead of cylinder)  units
-b  2048:  (for certain MO disks)  use  2048-bute  sectors
Winubul"winubul-desktop:¬$


Well it is Greek to me. but I'm here to learn.
                                                                                    Kevin

---

### Post by Cypher on 2007-05-30
That is very interesting, you did type "sudo fdisk -l"?? 

Let's try another thing then, in the terminal type
```

mount

```
and look for the harddrive markers such as "/dev/sda1" or "/dev/sdb1" or "/dev/hda1" and so on. Once you figure that out do
```

sudo fdisk -l <hard drive>

```
where <hard-drive> is "/dev/sda" or "/dev/hda" or whatever you figured out from the 'mount' command..

---

### Post by winubu on 2007-06-17
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec.nosuid,nodev)
/sys on /sys type sysfs (rw,noexec.nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec.nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw/mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw.gid=5,mode=620)
lrm on .lib/modules/2.6.17-17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---is the responce after typping mount


bash: syntax error near unexpected token 'newline'

----after I typed          sudo fdisk -1 <hard drive>

When trying to update to 7.04 I'm told I need to free 167m on  /var/cache/apt/archives/.
                                              and to empty trash and temps. using 'sudo apt-get clean'
but there is nothing there, as this is a new install.

Also I tried a new download through Downloads .com  It is wubi 18,956.00 mb
desinged to boot from a menu. ubuntu 7.04 or xp pro.
but it doesn't work also. But later about that.

thank you and please excuse the time laps in between.

---

### Post by Gwasanaethau on 2007-06-17
Unfortunately, I can't help with the initial problem, but I might be able to help with the last post. The first line you got after typing in 'mount' says something about /dev/hda1. I think Cypher meant you were to put that into the second command in place of '<hard drive>' (I could be wrong here!). This would give the command:
```
sudo fdisk -l /dev/hda1
```
Note also that the '-l' bit is the letter 'ell', not the number 'one' - it looks like you might have mistyped it in your last post.

P.S. I have no idea what that command does - I'm just trying to paraphrase what Cypher might have meant - so be careful in case it does something funny. Just thought I'd let you know! ;)

---

### Post by Gimpy_Rob on 2007-06-17
I've re-created your errors... all were simple transcription errors from this forum...

That last command by Gwasanaethau won't do anything, but he was on the right track.

ok, so, ```
sudo fdisk -l
```

That is the one command we really need to see to guage where your hard drive space is going. 
now, like Gwasanaethau said, it's "sudo fdisk -"THE LETTER ELL"  I only use caps to show where  the mistake was.  This will list out all drives that the computer sees.  

 The other is ```
df -h
```
this will list off all mounted partitions (which, from your last post, is only hda1) and what kind of space is free.

---

