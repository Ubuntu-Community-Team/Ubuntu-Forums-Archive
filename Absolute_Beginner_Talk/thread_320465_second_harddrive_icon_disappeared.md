---
title: "second_harddrive icon disappeared"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Troldmanden on 2006-12-17
yesterday I mounted a second harddrive for storage, and everthing worked out very nice, and ubuntu made a desktop-icon for the drive. But somehow today the icon is not there, and I cant quite figure out how to get it back, I tried searching in threads, but its seems like im the only one who have had this problem. Thanks !

---

### Post by taurus on 2006-12-17
If you mount it by hand, then you have to mount it each time you boot Ubuntu!  But if you want it to mount automatically, then you need to add an entry in /etc/fstab...

Now, what partition do you want to mount and where do you want to mount it to (with filesystem as well)?

---

### Post by Troldmanden on 2006-12-17
> **taurus said:**
> If you mount it by hand, then you have to mount it each time you boot Ubuntu!  But if you want it to mount automatically, then you need to add an entry in /etc/fstab...

Now, what partition do you want to mount and where do you want to mount it to (with filesystem as well)?

drive is /dev/hdb1 with one big partion
filesystem is ext3

where do I add the "/etc/stab" entry ?

---

### Post by Littleweseth on 2006-12-17
> **Troldmanden said:**
> drive is /dev/hdb1 with one big partion
filesystem is ext3

where do I add the "/etc/stab" entry ?

open the /etc/fstab file as the superuser. Fire up a terminal and type

sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab

Add this to your /etc/fstab :

/dev/hdb1 /mnt/hdb1 ext3 defaults,errors=remount-ro 0 1

use tab characters to separate the fields.

EDIT : I assume that you are using /mnt/hdb1 as your mount point. Substitute with the name of the mountpoint you're actually using. Also note that if you specify a mount point that doesn't exist, it will not be automatically created - use sudo mkdir /mnt/your-mount-name to create it.

---

