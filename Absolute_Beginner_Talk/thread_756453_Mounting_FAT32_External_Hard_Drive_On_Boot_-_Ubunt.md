---
title: "Mounting FAT32 External Hard Drive On Boot - Ubuntu Server"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by sds on 2008-04-15
I've Googled, and searched on these forums but to no useful end.

I have an external USB harddrive that I'm using on our headless media server running Ubuntu Server 7.10. I can mount it fine, it's never unplugged and therefore always at /dev/sdd. 

I want it to automount on startup so I added the following line to fstab. This mounts fine when running "mount -a" or "mount /mnt/backup" but it never seems to be mounted at boot!
```

# /dev/sdd1	
UUID=3717-D230	/mnt/backup	vfat	uid=network,gid=samba,umask=0003,defaults	0	0
```

Any ideas? Thanks in advance!

---

### Post by Diabolis on 2008-04-15
the "defaults" option should do it, anyway add "auto".

[more info here]("http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)")

---

### Post by sds on 2008-04-16
Tried adding auto, it didn't make it mount on startup.
Will have a look at the wiki, thanks.

---

### Post by sds on 2008-04-16
Okay, I've tried removing every option except for "auto" and still won't mount on boot! 

Likewise, I tried with their example of auto,umask=0000 and no difference (although it shouldn't have anyway).

It still mounts absolutely fine using 'mount'. 

Straight after bootup, it doesn't appear in 'mtab' or in the output from 'df -a' so I don't think something else is grabbing and mounting it.

Can anybody shed any light on this? I might just put it in an init script but it seems pointless when it should work as is!

---

### Post by sds on 2008-04-16
Right, I wasn't able to solve this normally so I created a basic init script. 
This might help someone having the same problem.

```
#!/bin/sh  
#  
# Mounting External Drive init control  
#  
#  
#  

# See how we were called.  
case "$1" in  
start)  
	# Start daemons.  
	echo -n \"Mounting /mnt/backup: \"  
	/bin/mount /mnt/backup
;;  
stop)  
	# Stop daemons.  
	echo -n \"Unmounting /mnt/backup: \"  
	/bin/umount /mnt/backup
;;  
restart)  
	$0 stop  
	$0 start  
;; 
*)  
	echo \"Usage: mnt-external {start|stop|restart}\"  
	exit 1  
esac  
exit 0
```

---

