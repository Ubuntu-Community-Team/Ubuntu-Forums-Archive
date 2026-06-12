---
title: "thumb drive files not deleting"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by mookie_jones on 2007-10-08
this may not be the correct forum for here but being that im completely new and giving it my best shot

Ive decided to go backwards to feisty instead of gutsy but i wanted to save a couple of files  to a 1gb thumbdrive. I deleted everything that was on there but it still tells me that i only have 30 mb free on the drive. what am i doing wrong? the only command i know to use is fdisk.

---

### Post by Crenfinkle on 2007-10-08
There is a hidden file on the thumb drive. When you open the window that shows the contents of the drive, press **Ctrl-H** and it will show a file called .Trash or something like that. Empty that folder and the files will be properly deleted.

---

### Post by mookie_jones on 2007-10-08
unfortunately thats not doing it but thanks for the tip

---

### Post by bsharp on 2007-10-08
That should do it but try this from the terminal:
```
sudo rm -R /*yourmountpoint* .Trash
```

---

### Post by dz0004455 on 2007-10-08
thats wierd, on mine, its stores everything in the .Trash-dz0004455 hidden folder on the drive.  Do you have proper permisions, and are you using some kind of strange flash drive?

---

### Post by mookie_jones on 2007-10-08
rm: cannot remove `.Trash': No such file or directory

---

### Post by mookie_jones on 2007-10-08
its a kingston thumb drive

---

### Post by macogw on 2007-10-08
cd to the flash drive and run "ls -A" and post the output

---

### Post by Dr Small on 2007-10-08
Try:
```
ls -la /media/*yourmountname*
```

If you see something named .trash466436546 or whatever, just run
```
sudo rm -R /media/*yourmountname*/.trash466436546
```

---

### Post by dz0004455 on 2007-10-08
sorry, i dont know anything else, wish i did

---

### Post by shad0w_walker on 2007-10-08
Have you tried just emptying your deleted items folder in the normal way? It works for me (It seems to show the contents of all my .Trash folders)

---

### Post by mookie_jones on 2007-10-08
im starting to question if i should be near a computer at all right this second.. I decided to reboot and now the drive wont show up at all

---

### Post by mookie_jones on 2007-10-08
> **shad0w_walker said:**
> Have you tried just emptying your deleted items folder in the normal way? It works for me (It seems to show the contents of all my .Trash folders)

what do you mean by this?

---

### Post by mookie_jones on 2007-10-08
mookie@mookie-ubuntu:~$ ls -la /dev/sdb
brw-rw---- 1 root plugdev 8, 16 2007-10-08 20:33 /dev/sdb

---

### Post by mookie_jones on 2007-10-08
if it helps

knoppix@Knoppix:~$ cat /etc/fstab
/proc      /proc       proc   rw,nosuid,nodev,noexec 0 0
/sys       /sys        sysfs  rw,nosuid,nodev,noexec 0 0
/dev/shm   /dev/shm    tmpfs  rw,nosuid,nodev,noexec 0 0
/dev/pts   /dev/pts    devpts mode=0622           0 0
/dev/fd0   /media/fd0  auto   user,noauto,exec,umask=000    0 0
/dev/cdrom /media/cdrom  auto   user,noauto,exec,ro 0 0
/dev/hdc /media/hdc  auto   users,noauto,exec,ro 0 0
# Added by KNOPPIX
/dev/hda1 /media/hda1 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/hda5 none swap defaults 0 0
# Added by KNOPPIX
/dev/sda1 /media/sda1 auto noauto,users,exec 0 0
knoppix@Knoppix:~$

---

### Post by kevin11951 on 2007-10-08
if you really want to get rid of everything try:
sudo apt-get install gparted
and use it to completely destroy everything on it... 
(for multi operating system compatibility, make one partition and make it fat32.)
also how big is it?

---

### Post by Linux_Man on 2007-10-08
Make sure your USB port isn't damaged, also what is it formated as?

---

