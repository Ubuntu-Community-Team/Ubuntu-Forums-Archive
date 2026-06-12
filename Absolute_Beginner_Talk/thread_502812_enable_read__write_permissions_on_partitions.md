---
title: "enable read / write permissions on partitions"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by hammad1337 on 2007-07-17
Here's the problem:
I have two fat32 partitions in my pc which I do not mount at boot time (I mount them when needed). These partitions are included in the the /etc/fstab. and are mounted in rw mode.
But when I try writing to them access is denied. I have even tried "chmod 777" and "chown" as root and su but even when the commands run without errors, the permissions are not changed.

should I try and run ```
chmod 777 /dev/sdax
``` instead of ```
chmod 777 /mount/folder
```

---

### Post by splintercellguy on 2007-07-17
It should be chown 777 -R /mount/folder. The -R means recursive.

---

### Post by jordanmthomas on 2007-07-17
Could we have a look at your fstab? 
Also, the output of 
```
ls -l /mount
```

**edit** and I wouldn't do a recursive chmod on it because FAT32 doesn't have the same permissions as Linux fliesystems and they're just set by the way you mount them and where you mount them, so it would be ineffective at best.

---

### Post by hammad1337 on 2007-07-18
/etc/fstab :
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
/dev/sda7     /               ext3        defaults    0   1
/dev/sda5       /media/host       vfat         defaults      0   0


/dev/sda6      none            swap        sw          0   0


```
ls -l  /media
```

total 16
drwxr-xr-x  2 root root 4096 2007-07-13 08:53 extra
drwxr-xr-x 15 root root 8192 1970-01-01 04:00 host
drwxr-xr-x  2 root root 4096 2007-07-13 08:53 tdm

```

---

### Post by steve.horsley on 2007-07-18
As jordanthomas says, FAT partitions can't store unix file permissions. So thay are emulated, and what velue to emulate is set as a mount option. Try changing "defaults" to "umask=0" for the vfat enties in /etc/fstab. Use the command **gksu gedit /etc/fstab **to edit the file. **DO NOT** change the ext3 entry. Try this for the vfat entry:
```
/dev/sda5       /media/host       vfat         umask=0      0   0
```

---

### Post by hammad1337 on 2007-07-18
Thanks a lot.
That worked. :)
May I also know what umask is and why setting it to 0 helps?

---

### Post by steve.horsley on 2007-07-18
First you need to understand the file mode - the number that sets the file permissions. Normal file permissions, at the most permissive are **rwxrwxrwx**, that is Read, Write and Execute three times - for Owner, Group and Others. This is represented numerically bu the number 777 (octal actually), each digit representing one group of 3 bits. A file where the owner has all rights, people in the file's group can read it, and no-one else can even read the file would be rwxr-----, or 740. The umode value given as a mount option is subtracted from 777 to give a resulting emulated fike permissions, and I think the default umode is 27, so ----w-rwx is subtracted from rwxrwxrwx, leaving rwxr-x---. 

If this sounds confusing, it's because I am explaining it badly. Google for unix file permissions and you should find lots of far more articulate explanations. There was a beautiful explanation last week here:
[http://ubuntuforums.org/showpost.php?p=2991546&postcount=3](http://ubuntuforums.org/showpost.php?p=2991546&postcount=3)

---

### Post by hammad1337 on 2007-07-19
Thanks a lot for all the info.

---

