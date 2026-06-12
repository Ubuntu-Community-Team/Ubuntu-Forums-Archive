---
title: "Automounting HFS+ partitions on boot"
date: 2005-07-06
forum: Apple PPC Users
---

### Post by audiorevolution on 2005-07-06
I'm trying to set my OSX HFS+ partitions to mount automatically when I boot.  My /etc/fstab is such:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda3       /mnt/osx        hfsplus noauto,user,rw  0       0
/dev/hda5       /mnt/files      hfplus  noauto,user,rw  0     0
```

I assume the problem is somewhere in "options."  hda3 does automount with the current settings, but it does not allow me to alter the filesystem, saying I don't have permission.  hda5 doesn't automount at all.  How can I alter the options to allow for this, and to give me permission?

---

### Post by Len on 2005-07-06
Here is a nice explanation if the man pages weren't enough:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I don't know if Linux supports HFS+ permissions, but if it does, it is logical that you can't modify your OS X filesystem. Most there is owned by root and your Mac OS X account...

You can of course always log in as root or use the 'sudo' command to bypass these permissions.

---

### Post by audiorevolution on 2005-07-07
Now, is there a way to get around permissions on these partitions?

---

### Post by paolo_ubu on 2005-07-07
log in as root?

---

### Post by Patchoulol on 2005-07-07
```

/dev/hda5       /mnt/files      hfplus  noauto,user,rw  0     0
```

Perhaps you should set the type to hfsplus and not hfplus ;)

---

### Post by Len on 2005-07-07
Damn... double post, sorry.

---

### Post by Len on 2005-07-07
:shock: :-# ...

Totally read over that one :P. Good spotting!

---

