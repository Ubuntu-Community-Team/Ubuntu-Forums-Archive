---
title: "help needed"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-03-04
previously my dvd was not detecting, when inserted the dvd in drive.
When later i typed "mount /media/cdrom0" my dvd was detecting
but i can not eject the dvd drive it says some thing like"can not eject the volume"
could u help me in removing the disk
and one more thing when i type this"ls -l /media" in terminal
i m getting

total 10
lrwxrwxrwx 1 root root 6 2008-03-03 12:01 cdrom -> cdrom0
dr-xr-xr-x 1 root root 10240 2008-03-03 17:35 cdrom0

could u help me please
and please tell me the reason why it happend so

---

### Post by laidback on 2008-03-04
You probably need to issue the umount command (think unmount but note spelling misses out the n)
$ umount /media/cdrom0

or if you have an icon on the desktop for the device then right click and choose Unmount from the list.

Also make sure any apps using the cd/dvd are shut down, i.e. closed. as you cannot umount a device that's in use.

---

