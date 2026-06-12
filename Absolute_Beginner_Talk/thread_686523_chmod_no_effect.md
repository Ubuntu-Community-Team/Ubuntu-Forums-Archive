---
title: "chmod no effect"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by bartkl on 2008-02-03
Hi,

I'm trying to set permissions to a file:
```

$ ls -l
-rwxrwxr-x 2 root plugdev     5759 2008-01-06 21:09 file.pun
$ sudo chmod 700 file.pun
$ ls -l
...
-rwxrwxr-x 2 root plugdev     5759 2008-01-06 21:09 file.pun

```

So, it has no effect. I also tried changing the owner and group of the files/dirs inside, but that didn't work out either!

```

$ chown -hR bart:musiclib /media/sda5

```

Afterwards it's still owned by root : plugdev. Weird thing too: plugdev isn't even an actual group when I manage my groups! It's not on the list.

Please help me, thanks.

---

### Post by taurus on 2008-02-03
What filesystem is /dev/sda5?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by bartkl on 2008-02-03
HPFS/NTFS is what the output of fdisk says.
In fstab it is NTFS.

---

### Post by jan quark on 2008-02-03
for the file permission try

```
sudo chown -R usr:usr CU
sudo chmod -R 755 CU
ls -la
```

change usr:usr to your username cu to the path to the file

---

### Post by bodhi.zazen on 2008-02-03
FAT / NTFS partitions do NOT support permissions.

They are set at the time of mount or in fstab with the options :

mount /dev /mount_point -o uid=xxx.gid=yyy,umask=007

or in fstab :

/dev /mount/pint ntfs-3g uid=xxx.gid=yyy,umask=007

Those permissions will be set for the entire partition.

See here : 

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by bartkl on 2008-02-03
Please reread my initial post, I have already ran chown with the parameters you suggest.
It didn't change anything. What your chmod suggestion concerns: chmod doesn't work for one file so it won't work for all. Thanks for your suggestions though.

(This was a reply to jan quark)

---

### Post by bartkl on 2008-02-03
> **bodhi.zazen said:**
> FAT / NTFS partitions do NOT support permissions.

They are set at the time of mount or in fstab with the options :

mount /dev /mount_point -o uid=xxx.gid=yyy,umask=007

or in fstab :

/dev /mount/pint ntfs-3g uid=xxx.gid=yyy,umask=007

Those permissions will be set for the entire partition.

See here : 

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

Thanks, that helps a lot :)
But then it seems impossible to configure permissions per file?

---

### Post by bodhi.zazen on 2008-02-03
> **bartkl said:**
> Thanks, that helps a lot :)
But then it seems impossible to configure permissions per file?

That is correct. When configure permissions (or directories) on NTFS (using umask or other options), the permissions you choose are set @ the time of mount for the **entire partition**.

---

### Post by bartkl on 2008-02-03
Okay, I understand that mounting hardware will cause all data on it to have equal permissions according to umask. The thing is though that what I do here (see initial post) IS concerning a single file. You say it is possible to set permissions per file even on NTFS media, please tell me how. As you can see in my initial post it doesn't just work the usual way. Or am I wrong somewhere?

Thanks again :)
Oh and how can I understand the umask notation? For instance, what  does umask=0002 mean? I've looked it up on Google but I can't find much. Perhaps one of you guys can give me a useful link or quick explanation. Thanks.

---

### Post by bodhi.zazen on 2008-02-03
links on umask : [http://www.ubuntuforums.org/showthread.php?&t=316704](http://www.ubuntuforums.org/showthread.php?&t=316704)

	[http://www.linuxsecurity.com/index2.php?option=com_content&do_pdf=1&id=117255](http://www.linuxsecurity.com/index2.php?option=com_content&do_pdf=1&id=117255)

I think we are failing to communicate.

NTFS does not support permissions. **You can not set the permissions of a single file on NTFS, period.** If you are wanting to do that, use a Linux native file system, like ext3.

You can set the ownership and permissions of the entire partition, and all the files and all the directories, bu using options at the time of mount. These options are set for the entire partition and can not be applied to a single file.

---

### Post by bartkl on 2008-02-04
I understand you now.

Thanks a lot :)

---

### Post by bodhi.zazen on 2008-02-04
I am happy we sorted it out, sorry I was unable to be more clear earlier.

---

