---
title: "[SOLVED] Just installed Feisty"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-30
I just installed Feisty and created a bunch of partitions. However, they all show up under 'File System'
 
I was assuming they would show up as different partitions like they do in windows. 
 
Has everything installed correctly in different partitions as I wanted?
 
I also cannot create any folders in the EXT3 partitions that I created, except for the /home folder

---

### Post by kejar31 on 2007-04-30
What are the partition names? was there a reason you set-up a bunch of partitions?

---

### Post by phidia on 2007-04-30
You probably are not the owner of the other partitions.  root owns the system and you pay rent for home. That's a joke. :)
Anyway if you want to change permissions on those partitions take a look at man chown & man chmod (typed in a terminal) or do sudo mkdir /the_partiton_location/new_directory name

---

### Post by Inxsible on 2007-04-30
I am the only user on the system as of now.
I created /home and /shared. I do see the folders in the File System and I can access them too. But I cannot create new folders in the /shared partition.
 
When we create partitions in Linux, don't they show up as different drives like in Windows (C:, D: etc) ?

---

### Post by phidia on 2007-05-01
Partitions will normally be labelled /mnt/hd?? e.g hda1 
Basically everything is a file in linux. Where is the shared directory mounted? 
In the terminal do ls -la /mnt/shared or any other files to see your permissions or select properties from the file manager and then open the permissions tab.
BTW windows and other linux installs are mounted and show up in "Places" with their partition designation. But if you create other partitions during the install process the installer sets them up as part of the system AFAIK and linux doesn't let the user(s) change system files only root can do that.

---

### Post by Inxsible on 2007-05-01
the shared directory is mounted in the root itself as /shared

ls -la /shared gives this:
Inxs@Inxs-laptop:~$ ls -la /shared
total 24
drwxr-xr-x  3 root root  4096 2007-04-30 18:24 .
drwxr-xr-x 23 root root  4096 2007-04-30 18:39 ..
drwx------  2 root root 16384 2007-04-30 18:24 lost+found

---

### Post by ubnewbie2 on 2007-05-01
> **Inxsible said:**
> 
When we create partitions in Linux, don't they show up as different drives like in Windows (C:, D: etc) ?


No they don't.  The concept of drive letters is gone.  Under linux/unix, everything is kept under the root folder "/" and is mounted to some mount point (folder).  So if you have a partition on a second IDE disk drive, it might have a name like hdb1, and you will see it in the special /dev folder, but that represents the unmounted device.  

It is mounted, either manually, or automatically according to the config in the /etc/fstab file,  to a mount point.  A mount point is just a folder you create, say /mnt/mydisk and can be mounted manually with something like

```
sudo mount /dev/hdb1 /mnt/mydisk
```

depending on permissions, you can then see it with 

```
ls /mnt/mydisk
```

and even change permissions.  To assume ownership, try

```
sudo chown -R <username> /mnt/mydrive
```

---

### Post by koconnor100 on 2007-05-01
> **Inxsible said:**
> I just installed Feisty and created a bunch of partitions. However, they all show up under 'File System'
 
I was assuming they would show up as different partitions like they do in windows. 
 
Has everything installed correctly in different partitions as I wanted?
 
I also cannot create any folders in the EXT3 partitions that I created, except for the /home folder

Paws off ! 

Those partitions are for the internal workings of Linux. I know one of them is strictly for memory swapping (linux uses a partition instead of a memory swap file). 

Plus you are just a user in your own system. Your home folder and everything under it is your domain , anything else, you're tinkering with the operating system and probably gonna crash it. 

You can tinker anyways with the sudo command (Super User Do ....) which runs one command as if you were the super user and overrides any permissions etc , but if you get into the habit of it AND tinker outside you're home directory with it too much .. well ...have your reinstall CD ready , you will be in need.

---

### Post by Inxsible on 2007-05-01
the 
```

sudo chown -R <username> /shared 

```
worked. Would I have to do this every time I log in ? Is there any way to make this permanent ?

---

### Post by ubnewbie2 on 2007-05-01
> **Inxsible said:**
> the 
```

sudo chown -R <username> /shared 

```
worked. Would I have to do this every time I log in ? Is there any way to make this permanent ?

Should be permanent.

---

