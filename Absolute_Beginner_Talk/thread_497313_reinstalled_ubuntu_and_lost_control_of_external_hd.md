---
title: "reinstalled ubuntu and lost control of external hd"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by wana10 on 2007-07-10
i had a problem a while back and have lost all control over my portable hd...unless i am the root user, and i don't like sitting in that chair for any length of time. 
after a power outage i was having some problems with my install and as i had been planning it anyways i decided to go ahead and reinstall ubuntu with a change from last time (seperate /home partition) upon booting in i 'sudo gedit /etc/fstab' and added the following to the bottom '/dev/sdb1 /home/wesley/external vfat 0 0' i then saved and exited. then i 'mkdir /home/wesley/external'. finally i 'sudo mount /dev/sdb1'. a lock emblem appears on the top right of my /home/wesley/external folder and suddenly only root can write in that folder. how can i change this so that my regular user account (wesley) has tha ability to write as well? i have tried 'sudo chmod 777 /home/wesley/external' and it tells me that i do not have the right to change access privleges for that folder.

---

### Post by pyros on 2007-07-10
> **wana10 said:**
> i had a problem a while back and have lost all control over my portable hd...unless i am the root user, and i don't like sitting in that chair for any length of time. 
after a power outage i was having some problems with my install and as i had been planning it anyways i decided to go ahead and reinstall ubuntu with a change from last time (seperate /home partition) upon booting in i 'sudo gedit /etc/fstab' and added the following to the bottom '/dev/sdb1 /home/wesley/external vfat 0 0' i then saved and exited. then i 'mkdir /home/wesley/external'. finally i 'sudo mount /dev/sdb1'. a lock emblem appears on the top right of my /home/wesley/external folder and suddenly only root can write in that folder. how can i change this so that my regular user account (wesley) has tha ability to write as well? i have tried 'sudo chmod 777 /home/wesley/external' and it tells me that i do not have the right to change access privleges for that folder.

I think you need to add the group you want to have access to the drive.

---

### Post by pyros on 2007-07-10
Yeah, this is what I had to do to get my drive to mount so that I could write to it without sudoing:
```

/dev/hdg1	/media/hdg1	ext3	rw,user,auto	0	0

```
rw = read/wrie
user = group with access
auto = auto mounts the volume

---

### Post by wana10 on 2007-07-10
cool, thank you for the help.

edit* went and tried this, still no dice. only root has write ability and it says i am not the owner of device and so cannot change permissions.

---

### Post by logos34 on 2007-07-10
> **wana10 said:**
> cool, thank you for the help.

edit* went and tried this, still no dice. only root has write ability and it says i am not the owner of device and so cannot change permissions.

how about:

**sudo chown -R <username>:<username> /home/wesley/external**

for fstab entry,try:

**/dev/sdb1 /home/wesley/external vfat iocharset=utf8,umask=000 0 0**

or better yet change the mount point to the standard one in media dir:

**/dev/sdb1 /media/wesley/external vfat iocharset=utf8,umask=000 0 0**

---

### Post by wana10 on 2007-07-10
ok i edited fstab to show

**/dev/sdb1 /media/external vfat iocharset=utf8,umask=000 0 0**

and mounted drive.
root still had exclusive write access to the drive so i 

**sudo chown -R wesley:wesley /media/external**

everyfile on the drive flashed through the terminal saying

**chown: changing ownership of '*file_name*': operation not permitted**

still nothing...bummer. thanks for the ideas though, i hadn't thought of chown.


edit* **FIXED IT!!! HOORAY** ok...maybe that was a little over the top but i'm happy darn it. :D changed my fstab entry to
**/dev/sdb1 /media/external vfat uid=1000,gid=wesley,defaults 0 0**
and now everything works. thanks for the help. the errors i got from those helped me refine my google search and get a working answer.

---

