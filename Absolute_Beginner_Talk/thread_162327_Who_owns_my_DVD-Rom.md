---
title: "Who owns my DVD-Rom"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by tansu on 2006-04-18
Hi, I am very new to ubuntu, I installed and upgraded succesfully. Installed amarok and mp3 codecs too. But when I tried to listen my DVD's it gave me that error sayin I dont have enough permission.
is this a joke or do not I own my DVD-Rom and mp3 files in it?

---

### Post by htinn on 2006-04-18
I don't think the file system is complaining that you don't "own" the disc. I think it's complaining that the permissions for the files you're trying to access do not allow you to have access.

---

### Post by unbuntu on 2006-04-18
[QUOTE=tansu]Hi, I am very new to ubuntu, I installed and upgraded succesfully. Installed amarok and mp3 codecs too. But when I tried to listen my DVD's it gave me that error sayin I dont have enough permission.
is this a joke or do not I own my DVD-Rom and mp3 files in it?[/QUOTE]

type the following command in console:
```

ls -l /media

```
and you should see a list of directories, similar to this
```

lrwxrwxrwx  1 root root     6 2006-04-01 08:59 cdrom -> cdrom0
[COLOR="Red"]drwxr-xr-x[/COLOR]  2 root root  4096 2006-04-01 08:59 cdrom0
dr-xr-xr-x  1 root root  8192 2006-04-16 22:33 hda1
dr-xr-xr-x  1 root root  8192 2006-04-16 22:05 hda5
drwxr-xr-x  3 root root  2048 1969-12-31 19:00 hda6
dr-xr-xr-x  1 root root 81920 2006-04-16 22:05 sda5
dr-xr-xr-x  1 root root  8192 2006-04-16 22:05 sda6
drwxr-xr-x  2 root root  4096 2006-04-17 16:31 vcd

```

See the highlighted portion?  That's the access mode given to this directory.  
Interpretation: (from left to right, bit by bit)

Directory? | owner_read | owner_write | owner_executable | group_read | group_write| group_excutable | all_read | all_write | all_executable

If you see the bit at all_read is "-", that means you don't have the permission to read from this directory.

To solve this, check your /etc/fstab file
```

cat /etc/fstab

```

look for a line similar to this:
```

/dev/hdc        /media/cdrom0   udf,iso9660[COLOR="Red"] user[/COLOR],noauto     0       0

```

Make sure you have "user" option turned on.

If not, add this line (need sudo)

after that, unmount all the partitions:
```

sudo umount -a

```

remount everything automatically from /etc/fstab:
```

sudo mount -a

```

HTH

---

