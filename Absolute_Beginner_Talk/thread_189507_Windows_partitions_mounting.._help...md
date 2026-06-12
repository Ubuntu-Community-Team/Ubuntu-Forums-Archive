---
title: "Windows partitions mounting.. help.."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by madu on 2006-06-05
Hi guys..

I'm having a problem with my windows partions mounting everytime I start Ubuntu. How can I make it not do that..?

Here's my /fstab:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb3       /media/sdb3     ext3    defaults        0       2
/dev/sdb5       /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb6       /media/sdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0[/B]


Thanks a lot guys..

---

### Post by Sutekh on 2006-06-05
[quote=madu]Hi guys..

I'm having a problem with my windows partions mounting everytime I start Ubuntu. How can I make it not do that..?[/quote] 
Not mount at startup?

Add the **noauto** option to the /etc/fstab entries, ie
```
/dev/sda1       /media/sda1     ntfs    **noauto,**defaults,nls=utf8,umask=007,gid=46 0       1
```
Or comment them out, by adding a # sign to the beginning of the line.

---

### Post by madu on 2006-06-05
Thank you Sutekh.. will do that..!

---

### Post by Sutekh on 2006-06-05
I'm not sure if the **noauto** option will conflict with the **defaults** option, which includes the **auto** option.

I guess we will know soon.

You can get some really good detail on mounting options from the mount manual```
man mount
``` or online

[http://www.die.net/doc/linux/man/man8/mount.8.html]("http://www.die.net/doc/linux/man/man8/mount.8.html")

---

### Post by steve.horsley on 2006-06-05
[QUOTE=Sutekh]I'm not sure if the **noauto** option will conflict with the **defaults** option, which includes the **auto** option.

[/QUOTE]
I think that "defaults" is just a do-nothing place-holder for when there are no non-default options. Because it's a space-separated file format, you **have** to have some kind of text there.

---

### Post by Sutekh on 2006-06-05
I only said it because of the man page...

[quote=mount man page]
**defaults** 
[INDENT]           Use default options: **rw**, **suid**, **dev**, **exec**, **auto**, **nouser**, and **async.**[/quote] 
[/INDENT] Do you suppose **noauto** replaces *all* of the **defaults** or just it's opposite; **auto**?

---

