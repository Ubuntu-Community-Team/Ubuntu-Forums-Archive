---
title: "UBUNTU disks manager"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by anders600 on 2006-02-24
From Windows to Linux .. and a lot of questions then .. :)

1.
I have a PC with 3HDD and UBUNTU installed on one of them. I have created a map called /ext. In this one I have created /ext/disk1 and /ext/disk2.  I have created these as user.

Disks manager lest me set these as access paths to my hard drives.
hda1 -> /
hdb1 -> /ext/disk1
hdd1 -> /ext/disk2
I have also set these accesible. All of this is performed by root.

Now, the problem is that it is not possible to change the right of /ext/disk1 or /ext/disk2. The all have permission 755. I would either like to change the owner from root to user or sett permissions 777 on these folders. But how to do it?

2.
One more problem. I would like to control this computer via VNC, and have no monitor connected, but then I can only have the resolution 640*480. And it is not possible to change this the "Screen resolution" app. Please help me! :)

Thanks!

---

### Post by sas on 2006-02-25
Hi,
Unfortunatly there is no graphical interface to do this. the reason you can't change the permissions to be 777 is that there is a 'umask' set which stops the permissions changing to certain digits.

You need to edit the /etc/fstab file using sudo, and change the umask to 000.

If this sounds a bit much see [http://help.ubuntu.com/starterguide/C/ch05.html#id2532903](http://help.ubuntu.com/starterguide/C/ch05.html#id2532903) for the exact instructions.

If you can't get it working please reply :)

---

