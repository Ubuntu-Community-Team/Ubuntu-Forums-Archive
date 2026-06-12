---
title: "Boot problem checkfs log generated"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Doggles on 2007-11-14
Hi folks

During bootup (Gutsy) - I get an error message saying that an error log has been created in var/log/fsck/checkfs - here's what the log says:

Log of fsck -C -R -A -a 
Wed Nov 14 19:25:11 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 28338/16924672 files, 24875597/33836898 blocks (check after next mount)
/dev/sda2: clean, 4890/12107776 files, 12459628/24199914 blocks
fsck.ext3: Unable to resolve 'UUID=blah-blah-blah...f'

fsck.ext3: Unable to resolve 'UUID=different blah-blah-blah...'

fsck died with exit status 8

Wed Nov 14 19:25:12 2007
----------------

The blah-blah-blahs are edited out cos I didn't know if they were a security risk o a forum!

Help - don't really understand this one...

I've been installing other distros here and there, maybe one of them broke something?

Cheers

---

### Post by Inxsible on 2007-11-14
open up a terminal and type in ```
gksudo gedit /etc/fstab
```
See if the UUIDs match with the partitions.

---

### Post by Doggles on 2007-11-14
Here's the output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=154a667e-0e58-42b9-9527-e24bd4204bad /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=f82a3111-13f7-4f7b-93be-b6508d8449eb /home           ext3    defaults        0       2
# /dev/sda4
UUID=ace78f7a-25d7-48dd-ab13-ebd2be8c58af /media/sda4     ext3    defaults        0       2
# /dev/sdb2
UUID=f852674a-a4d5-4ae6-9f77-5cdec1c75761 /media/sdb2     ext3    defaults        0       2
# /dev/sdb1
UUID=7816c323-e99e-4a91-8eed-65e88675a98f /storage        ext3    defaults        0       2
# /dev/sda3
UUID=e69682fe-ed9d-4283-a2bf-030ce2dc0819 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Any clues?

---

### Post by Doggles on 2007-11-15
Oh.. hang on, I think I understand what you meant now... match the UUIDs to the original error log - right?, will have to wait til I get home from work though - thanks for your help so far - I'll repost when I've had another look...

PJ

---

### Post by Doggles on 2007-11-15
Yep - it looks like the two UUID codes that are giving the error correspond to 2 of my other installed distros (one is Mepis, the other OpenSUSE) - one installed before Gutsy, one after...

Any way to fix this? - after ctrl+D to get out of the error report, Gutsy boots up fine and all the partitions can be accessed, so it's clearly not a major problem - any way to get it to just ignore this?

---

### Post by Doggles on 2007-11-16
bumpity bumplington?

---

### Post by Doggles on 2007-11-16
OK so I found a thread that helps with this in case anyone has the same problem - see: [http://ubuntuforums.org/showthread.php?t=599546&highlight=resolve+UUID](http://ubuntuforums.org/showthread.php?t=599546&highlight=resolve+UUID)

---

