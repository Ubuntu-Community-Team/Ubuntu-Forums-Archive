---
title: "storage partition doesn't show up when i reboot"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by h-town on 2007-12-26
I made a storage partition from the space that was formally used by vista.

I've formated it ext3, and i've mounted it using fstab.

What's missing? Do i make a change to Grub so it always shows up when I boot the system?

---

### Post by Moop on 2007-12-26
Where did you mount it?

If you mounted it in your media directory it should be there in the File System.

---

### Post by Cypher on 2007-12-26
Having the partition properly listed in the FSTAB file is all you need to make a partition mount automatically during bootup.

You can go to the command prompt and type
```

sudo mount -a

```
and if the partition shows up, then the FSTAB file is fine and there is something else wrong, if the partition doesn't show up, the FSTAB might not be correct. Post your FSTAB contents and we might help debug it for you..

---

### Post by h-town on 2007-12-26
harrison@The-Zone:~$ sudo mount -a
[sudo] password for harrison:
harrison@The-Zone:~$ sudo mount -a
harrison@The-Zone:~$ 

nothing happened. 

and i *think* i mounted it in the media directory.

---

### Post by Cypher on 2007-12-26
The mount command will succeed quietly and only print something on errors..so let's try this approach instead..reboot the box and run the following commands
```

df -h
sudo mount -a
df -h

```

This will list the currently mounted partitions/drives, then mount everything and list them again. We should see a change between the two "df" commands..

---

### Post by h-town on 2007-12-26
harrison@The-Zone:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              62G   43G   16G  74% /
varrun               1009M   96K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda2              74G  581M   70G   1% /storage
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0
harrison@The-Zone:~$ sudo mount -a
[sudo] password for harrison:
harrison@The-Zone:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              62G   43G   16G  74% /
varrun               1009M   96K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda2              74G  581M   70G   1% /storage
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0
harrison@The-Zone:~$

---

### Post by h-town on 2007-12-26
sda2 is the old vista partition.

---

### Post by Cypher on 2007-12-26
From the output of your first "df -h", it looks like SDA2 is mounted properly on /storage, so the automatic mounting is happening.

You can do also a "sudo fdisk -l" to ensure that the new SDA2 is of type EXT2/EXT3..other than that, you should be now able to use the /storage directory..

You might have to CHOWN that particular directory to your username if you want to use it as a storage dump..

---

### Post by logos34 on 2007-12-26
or to show fs type 

df -hT

the standard mount point is in /media

---

### Post by h-town on 2007-12-26
the partition still isn't showing up when I go to places/computer

how do i use the chown command?

---

### Post by Cypher on 2007-12-26
From the command line
```

cd /
ls -l
sudo chown <username> /storage
ls -l

```

---

### Post by h-town on 2007-12-26
harrison@The-Zone:/$ sudo chown <harrison> /storage
bash: harrison: No such file or directory
harrison@The-Zone:/$ sudo chown <username> /storage
bash: username: No such file or directory
harrison@The-Zone:/$

---

### Post by h-town on 2007-12-26
that last thing i did seems to have done something bad, now my computer is restarting on it's own randomly.

---

### Post by Cypher on 2007-12-26
The command would be
```

sudo chown harrison /storage

```
the <> was just me telling you to fill in your username..:)

The two commands you did both failed, so nothing should've changed and as such that in particular shouldn't be causing your computer to reboot randomly..

---

### Post by h-town on 2007-12-26
oh, haha.. yeah i'm new to terminal. So I did what you said:

harrison@The-Zone:~$ cd /
harrison@The-Zone:/$ ls -l
total 96
drwxr-xr-x   2 root     root      4096 2007-11-26 18:44 bin
drwxr-xr-x   3 root     root      4096 2007-12-19 15:37 boot
lrwxrwxrwx   1 root     root        11 2007-11-26 18:30 cdrom -> media/cdrom
drwxr-xr-x  13 root     root     13940 2007-12-26 14:58 dev
drwxr-xr-x 124 root     root     12288 2007-12-26 13:42 etc
drwxr-xr-x   4 root     root      4096 2007-12-20 23:20 home
drwxr-xr-x   2 root     root      4096 2007-10-15 19:17 initrd
lrwxrwxrwx   1 root     root        33 2007-11-26 18:43 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root     root     12288 2007-12-10 21:49 lib
drwx------   2 root     root     16384 2007-11-26 18:30 lost+found
drwxr-xr-x   3 root     root      4096 2007-12-26 13:42 media
drwxr-xr-x   2 root     root      4096 2007-10-08 06:47 mnt
drwxr-xr-x   2 root     root      4096 2007-10-15 19:17 opt
dr-xr-xr-x 146 root     root         0 2007-12-26 08:42 proc
drwxr-xr-x   9 root     root      4096 2007-12-19 15:59 root
drwxr-xr-x   2 root     root      4096 2007-12-10 21:48 sbin
drwxr-xr-x   2 root     root      4096 2007-10-15 19:17 srv
drwxr-xr-x   3 harrison harrison  4096 2007-12-20 21:10 storage
drwxr-xr-x  12 root     root         0 2007-12-26 08:42 sys
drwxrwxrwt  16 root     root      4096 2007-12-26 17:33 tmp
drwxr-xr-x  11 root     root      4096 2007-10-15 19:19 usr
drwxr-xr-x  15 root     root      4096 2007-10-15 19:31 var
lrwxrwxrwx   1 root     root        30 2007-11-26 18:43 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
harrison@The-Zone:/$ sudo chown harrison /storage
[sudo] password for harrison:
harrison@The-Zone:/$ ls -l
total 96
drwxr-xr-x   2 root     root      4096 2007-11-26 18:44 bin
drwxr-xr-x   3 root     root      4096 2007-12-19 15:37 boot
lrwxrwxrwx   1 root     root        11 2007-11-26 18:30 cdrom -> media/cdrom
drwxr-xr-x  13 root     root     13940 2007-12-26 14:58 dev
drwxr-xr-x 124 root     root     12288 2007-12-26 13:42 etc
drwxr-xr-x   4 root     root      4096 2007-12-20 23:20 home
drwxr-xr-x   2 root     root      4096 2007-10-15 19:17 initrd
lrwxrwxrwx   1 root     root        33 2007-11-26 18:43 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root     root     12288 2007-12-10 21:49 lib
drwx------   2 root     root     16384 2007-11-26 18:30 lost+found
drwxr-xr-x   3 root     root      4096 2007-12-26 13:42 media
drwxr-xr-x   2 root     root      4096 2007-10-08 06:47 mnt
drwxr-xr-x   2 root     root      4096 2007-10-15 19:17 opt
dr-xr-xr-x 146 root     root         0 2007-12-26 08:42 proc
drwxr-xr-x   9 root     root      4096 2007-12-19 15:59 root
drwxr-xr-x   2 root     root      4096 2007-12-10 21:48 sbin
drwxr-xr-x   2 root     root      4096 2007-10-15 19:17 srv
drwxr-xr-x   3 harrison harrison  4096 2007-12-20 21:10 storage
drwxr-xr-x  12 root     root         0 2007-12-26 08:42 sys
drwxrwxrwt  16 root     root      4096 2007-12-26 17:33 tmp
drwxr-xr-x  11 root     root      4096 2007-10-15 19:19 usr
drwxr-xr-x  15 root     root      4096 2007-10-15 19:31 var
lrwxrwxrwx   1 root     root        30 2007-11-26 18:43 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
harrison@The-Zone:/$ 

so do I have to restart my computer or something, because I'm afraid places/computer still refuses to acknowledge that I do, indeed, have another partition.

---

### Post by h-town on 2007-12-27
stuck in a rut.. any ideas gentlemen?

---

### Post by h-town on 2007-12-28
bump it up.. ?

looks like i'll just have to reinstall ubuntu, oh well.. thanks for your help

---

