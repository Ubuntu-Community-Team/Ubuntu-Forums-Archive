---
title: "mount fat partition as user"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by AGSzabo on 2007-02-14
what should i write into my fstab to mount fat partitions with read and write access by all users?
currently if mounted all files seem to belong to root...

btw, my system stops booting when i enter 1 at the <pass> field for my fat partitions. the system stops booting and a text appears "checking filesystems" (or similar) but nothing really happens until i press ctrl-alt-del (then system continues booting...).


this is my fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=b0ab36f7-48a0-4a61-93ec-3dcea57eab42 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=12d411fc-cce6-4db5-91d3-b33c01f9f19a /boot           ext2    defaults        0       2
# /dev/hda7
UUID=0BAD-8BDC  /media/dir      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=c585fbc6-3b1b-48d2-bea2-97f421b6fd7e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/           /media/floppy1  auto    rw,user,noauto  0       0

/dev/hdb6       /media/temp      vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hdb5       /media/medien    vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hdd1       /media/320gb     vfat    defaults,utf8,umask=007,gid=46 0       0

---

### Post by taurus on 2007-02-14
```

/dev/hdb6 /media/temp vfat iocharset=utf8,umask=000 0 0
/dev/hdb5 /media/medien vfat iocharset=utf8,umask=000 0 0
/dev/hdd1 /media/320gb vfat iocharset=utf8,umask=000 0 0

```

---

### Post by AGSzabo on 2007-02-14
thank you. that was really faast. but why did you modify the charset part, too and why did you omit the defaults and the gid part?

---

### Post by dannyboy79 on 2007-02-14
he got rid of defaults because that means that these mount options would apply then:
defaults = rw, suid, dev, exec, auto, nouser, and async.

you can reads all about fstab here. it's a good read and very informational. I don't agree with him removing the gid and I would also have added the uid option. so my vfat partitions are as follows:


/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0

but that's just me, and I am sure that taurus has a good reason as he is very knowledgable.

---

### Post by AGSzabo on 2007-02-14
if i only kew his reasons... but thank you, too :)

i think you wanted to post a link but forgot?

---

### Post by dannyboy79 on 2007-02-14
oh yeah, sorry, here it is: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

it was found using gogle. gogle and the search function at the top of the forum have all the answers and you also learn more stuff by searching for your answer instead of asking someone for the answer. you'll pick up on linux faster this way but there are many users to help you if you don't find a suitable answer in gogle or the search function.

---

### Post by AGSzabo on 2007-02-18
> /dev/hdb1 /home/daniel/fat32 vfat rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0


during boot i get the message that utf8 is NOT a recommended charset for a fat partition. huh...

---

