---
title: "Error with &quot;file:///home&quot;"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Paul Bennett on 2006-04-11
Hey guys. '

Im currently running the latest flight of Kubuntu Dapper on ym sony vaio laptop. I get the following error when I open almost anything: "home folder", "storage media", or "users forlders". I also get this when opeing things like my flash drive.

[img]http://img226.imageshack.us/img226/3457/error1qv.jpg[/img]

When setting up kubuntu, I made three partitions. (/) about 6GB, (/home) about 7GB, and a swap partition. Is this correct? All opf these are on a same hard drive as my windows XP installation.

Any ideas what might be going on? I will be more than happy to provide any more information needed. 

Thank you very much for your help.

Paul

---

### Post by Mustard on 2006-04-11
Can you please paste the contents of your /etc/fstab file in here?

Via the command line you can do this to get the contents...

```
cat /etc/fstab
```

I'm curious to see what partition you have mounted and what mount points you have designated for those partitions.

---

### Post by Paul Bennett on 2006-04-11
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

Thanks!

---

### Post by Mustard on 2006-04-12
Hmm..well nothing wrong there.  Except perhaps that you might have some permission problems with your ntfs partitions.  Your /home partition should be fine though. I'd be only guessing at this stage what it could be.

---

### Post by Paul Bennett on 2006-04-12
Yes. I noticed that I could not access any of the nfts partitions (windows XP). How can I acccess them so that I can read (even write?) to them from linux?

I tried the permissions tab of the properties box, but It wont let me change the permissions. "could not enter folder lalala."

---

### Post by taurus on 2006-04-12
If you want a regular user to be able to read (not write unless you want your NTFS damaged!!!) your NTFS, then you need to modify your /etc/fstab, especially the entries for /dev/hda1 & dev/hda2.
```

/dev/hda1       /media/hda1     ntfs    defaults,umask=0222        0       0
/dev/hda2       /media/hda2     ntfs    defaults,umask=0222        0       0

```

---

### Post by Paul Bennett on 2006-04-12
Thanks. If I do that will I **be able** to write to the partition accidently? I want to not be able to accidently mess anything up.

---

### Post by taurus on 2006-04-12
Nope.  You only have permission to read, not write so don't worry about messing up your NTFS partitions...  ;)

---

### Post by Paul Bennett on 2006-04-12
I typed everything as you said (basically, added "umask=0222"), yet I still get 

```
could not enter folder /media/hda1.
```

Any Ideas?

Thanks again.

---

### Post by taurus on 2006-04-12
[QUOTE=Paul Bennett]I typed everything as you said (basically, added "umask=0222"), yet I still get 

```
could not enter folder /media/hda1.
```

Any Ideas?

Thanks again.[/QUOTE]
Did you reboot?

---

