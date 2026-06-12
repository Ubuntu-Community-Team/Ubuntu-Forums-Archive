---
title: "help with mounting drives"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by meatsheets on 2007-08-25
i reformatted my hard drive using kparted into ext3. it mounts fine, but i cant write anything onto the hard drive or create folders.

please help

---

### Post by Happy_Man on 2007-08-25
Hmm..... try these commands:

```
sudo mkdir /media/drive
sudo mount -t ext3 /dev/sda<partition number> /media/drive
chmod u+x /media/drive
```

---

### Post by meatsheets on 2007-08-26
for the sudo mkdir /media/drive
it says :mkdir: cannot create directory `/media/drive': File exists
for the sudo mount -t ext3 /dev/sda1 /media/drive
its says: mount: /dev/sda1 already mounted or /media/drive busy
mount: according to mtab, /dev/sda1 is already mounted on /media/drive
and for the chmod u+x /media/drive
nothing happened

---

### Post by Happy_Man on 2007-08-26
Either way, the last command was the one that changed the permissions. See if it works now.

---

### Post by meatsheets on 2007-08-26
i tried to move a file into it and it said
You do not have permissions to write to this folder.

---

### Post by meatsheets on 2007-08-26
i tried the last command again
and it said
chmod: changing permissions of `/media/drive': Operation not permitted

---

### Post by Diabolis on 2007-08-26
Unmount your partition, change the owner of your mount point and then mount again.

```
sudo umount [partition path]
chown username [mount point]
mount [partition]
```

---

### Post by meatsheets on 2007-08-26
jake@hacksaw:~$ chwon jake /media/drive
bash: chwon: command not found

did i type that in right?

---

### Post by Diabolis on 2007-08-26
I'm very very sorry, I didn't notice the typo. I just edited my last post. The correct command is **chown**. Again sorry for the inconvenience.

---

### Post by meatsheets on 2007-08-26
i tried that and now the drive owner is unknown mounted and unmounted

---

### Post by Diabolis on 2007-08-26
I assume you'll be doing all this using the sudo command, right? and in this order:
umount, change owner and mount again. 
Also this time try changing the permissions too (before mounting) like this:
```
sudo chmod 7777 /media/disk
```

You can verify if you'll have write permissions even before mounting your partition. Navigate to the /media folder and check if you can create a file in the disk folder.

---

### Post by meatsheets on 2007-08-26
i got it
i used gksudo nautilus
and fixed the properties from there
thanks alot for all of your guys's help!

---

