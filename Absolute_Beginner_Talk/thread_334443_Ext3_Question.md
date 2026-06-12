---
title: "Ext3 Question"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by ScottMorris on 2007-01-08
Ok, i have a really stupid question, but here it goes.  I want to mount my fresh Ext3 partition.  But I can't figure out  what to put in the fstab, so far I have ```
/dev/hda4	/media/hda4	ext3	{need mounting options} 	0       1
```  I want it auto mounted and be able to read and write to it.

Thanks for the help.

---

### Post by c-ron on 2007-01-08
'defaults' is a good one. I have my root partition set with 'defaults,errors=remount-ro'. Hope this helped.

---

### Post by STREETURCHINE on 2007-01-08
you could do
                               /dev/hda4      media/shared       ext3     defaults   0      1


                               sudo mkdir /media/shared
                               sudo mount -a
                                sudo chmod -R  777 media/shared
                                 df -h

---

### Post by aysiu on 2007-01-08
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) should help.

---

### Post by moshuptrail on 2007-01-08
defaults 

ought to do it

---

### Post by ScottMorris on 2007-01-08
Thanks for the response, that is what my root has, but this partition is a secondary Ext3 partition and when I try that for this one I can read it, but not write.

Here is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d58be31f-85d0-435c-8c5c-ae6b646ab8dc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=40F8F50BF8F4FFC8 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
#UUID=80b2ad10-c091-4eda-b542-2a9b713a07c4 none            swap    sw              0       0
/dev/hda3	swap		swap	defaults	0	0

# /dev/hda4
/dev/hda4	/media/hda4	ext3	{need mounting options} 	0       1

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by ScottMorris on 2007-01-08
> **STREETURCHINE said:**
> you could do
                               /dev/hda4      media/shared       ext3     defaults   0      1


                               sudo mkdir /media/shared
                               sudo mount -a
                                sudo chmod -R  777 media/shared
                                 df -h
Thanks, that works, but is there a way I can encode that into the fstab, or do I just need defaults and the mount will still be readable and writeable.

---

### Post by STREETURCHINE on 2007-01-08
you just need defauts

---

### Post by ScottMorris on 2007-01-08
Thanks so much everyone.:-D

---

