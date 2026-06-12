---
title: "help, Ubutu does not shutdown cleanly"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by blu3ness on 2007-05-29
Hello All, I have experienced problems with shutting down ubuntu recently, it appears that it does not shutdown properly. For example, whenever I start up ubuntu, I'll be forced to check my hda2 boot partition for damages etc and the system says that "the partition was not cleanly unmounted."

I tried to get some info from the systems logs, and here are some that's somewhat relevant
```


May 29 18:40:37 localhost kernel: [    8.568000] swsusp: Resume From Partition 3:3
May 29 18:40:37 localhost kernel: [    8.568000] PM: Checking swsusp image.
May 29 18:40:37 localhost kernel: [    8.568000] PM: Resume from disk failed.
```

menu.lst from grub
```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=89a661b2-0611-4982-a34b-15e746674a7f ro quiet splash rootflags=data=writeback
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

fstab file
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=89a661b2-0611-4982-a34b-15e746674a7f /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0 1
# /dev/hda1
UUID=62384ABC384A8F4B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=61a43832-4004-45c4-abe4-cc1f522fabb4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#192.168.1.100:/home    /home/bolu/work/  nfs       rw,hard,intr        0       0


```

---

### Post by sankarv on 2007-05-30
try 

> 
init 6



from command line for safe reboot


and then shut down 


using 


> 
init 0


from command line.

then restart and check it. it worked for me when i was facing similar problem before.

---

