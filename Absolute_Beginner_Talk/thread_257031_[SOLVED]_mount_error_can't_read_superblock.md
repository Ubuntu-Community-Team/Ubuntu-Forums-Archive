---
title: "[SOLVED] mount error: can't read superblock"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-09-13
Hello everybody,
I have really hard times to get packet writing installed properly. I tried everything following all the instruction in [dradul's HOWTO]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+Writing+tears") (where I posted all the details of my struggle). 
I can not get over the hurdle of mounting the drive.
The command ```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0

```always leads to the error message> [COLOR="Red"]**mount: /dev/pktcdvd/0: can't read superblock**[/COLOR]I don't know where the mistake is. This is my /etc/fstab, which is probably responsable for the trouble, but I can not figure out why:
> # /etc/fstab: static file system information.
#
#<file system> <mount point>   <type>   <options>          <dump>  <pass>

## Linux 'Ubunu 6.06'
proc             /proc           proc     defaults             0       0
/dev/sda2        /                ext3    defaults,errors=remount-ro 0       1
/dev/sda3        /Storage         ext3    defaults             0       2
/dev/sda1        /boot            ext3    defaults             0       2
/dev/sda5        /home            ext3    defaults             0       2
/dev/sda6        /usr             ext3    defaults             0       2
/dev/sda7        /var             ext3    defaults             0       2
/dev/sda8        none             swap    sw                   0       0

/dev/hda      /media/cdrom1    iso9660,udf   rw,users,noauto        0      0
/dev/hdb      /media/cdvdrw    iso9660,udf   rw,users,noauto        0      0

/dev/pktcdvd/0  /media/udf0   udf    users,noauto,noatime,utf8  0      0
/dev/pktcdvd/1  /media/udf1   udf    users,noauto,noatime,utf8  0      0
Please, can somebody help me here! I'm dealing with this issue since last week and there was nobody yet able or willing to give me a hint.
The hint I got from dradul> You may need to disable the other, default, entries. The message means that the cd has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.I didn't understand, because I don't know what it means and how to "disable default entries"
**I know I'm close and I don't want to give up!!!**

---

### Post by Cariboo1938 on 2006-09-18
> **Cariboo1938 said:**
> Hello everybody,
  I don't know where the mistake is.Please, can somebody help me here! I'm dealing with this issue since last week and there was nobody yet able or willing to give me a hint.
The hint I got from [dradul]("http://www.ubuntuforums.org/showpost.php?p=1476368&postcount=14") I didn't understand, because I don't know what it means and how to "disable default entries"
**I know I'm close and I don't want to give up!!!**:-\" Case closed! ... Packet Writing works...

I had to mount a CD and not the CD drive, because the CD has the File System on it I wanted to use...UDF.
The solution is:
When executing the command
Code:
*sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0*

the formatted CD has to be inserted in the corresponding drive!

---

