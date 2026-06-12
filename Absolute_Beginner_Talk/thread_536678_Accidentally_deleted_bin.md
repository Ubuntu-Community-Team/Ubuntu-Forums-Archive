---
title: "Accidentally deleted /bin"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ajmedfor on 2007-08-28
I am an idiot and accidentally pressed delete while I was running nautilus as superuser to transfer some system files. Is there any way I can retrieve the contents of /bin without completely re-installing? Would it work if I just did a fresh install on a blank partition, then copied the files to /bin using the live disk or something? Please help, because Windows is making me sick.

---

### Post by Perfect Storm on 2007-08-28
You could check  in /root/.Trash and put it back if it's there.

---

### Post by benhall on 2007-08-28
If you can't get your system to run without /bin, follow artificial intelligence's advice by using a live cd and manually mounting the root partition. Open a terminal, type

> sudo -s

To become root. Then go to /media, create a directory there to mount your root partition to and then mount it (here /dev/sda1 is your root partition)

> 
cd /media
mkdir ubuntu-root
mount /dev/sda1 /media/ubuntu-root


You can then navigate into this directory to find the trash file. It will be located in /media/ubuntu-root/root/.Trash. If the contents of the directory are not what you expected, or you get an error mentioning swap you probably have mounted the wrong partition. Try to unmount it if necessary and then mount an alternative partition

> umount /media/ubuntu-root
mount /dev/sdb1 /media/ubuntu-root

Don't forget to unmount the drive when you are finished before rebooting the live cd, for safety's sake.

---

