---
title: "Need help with sudo, root things..."
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by yogasades on 2007-02-07
Hi! I am a real newbie with Linux. Have been trying to work this OS out for the last 8 hours. 

I have installed everything and I would like to access the files that I have on the other drive (NTFS/Win XP).

Since I found that there is no Disks Manager (stated in the help center) on the latest version (6.10), I mounted the drive through the terminal. Problem is I can not access the folder through the GUI!!

I tried accessing it through the terminal (with all those sudo things), it worked! I can access it through the terminal. However, through the GUI, it said, "You do not have the permission necessary to view the folder....". 

It seemed to me that my account made during the installation does not have "root" privileges. If so, how do I set so that my account have the same privileges as the "root" account? 

The other thing is that, I can't even login with the "root" account to the GNOME. It said, "System Administrators are not allowed to login through this...". 

Can someone help me out with this?

Thank you.

---

### Post by Brunellus on 2007-02-07
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

will have all the information you need.

---

### Post by yogasades on 2007-02-07
Oh.. Ok, i think i got a few of the points now.

Sorry but is it possible to give "privileges" to specific accounts? Ex. I would like my account to be able to mount drive instead of root account only.

Anyway, thank you for the fast answer!

---

### Post by Brunellus on 2007-02-07
provided you make the mount point inside a directory you have permission to work in--say, your home directory--you can do whatever you need.

---

### Post by yogasades on 2007-02-07
I tried it to my home directory, but it still doesn't work. It says, "mount: only root can do that".

It seemed to me that my account does not have the privilege to mount anything at all.

---

### Post by Brunellus on 2007-02-07
> **yogasades said:**
> I tried it to my home directory, but it still doesn't work. It says, "mount: only root can do that".

It seemed to me that my account does not have the privilege to mount anything at all.
fair enough.  you should be able to do it with sudo mount

sudo gives your user root privileges for a limited time--and it writes logs of all of those instances in /var/log/auth.log.  It will do the job, and will not require you to become root.

---

### Post by yogasades on 2007-02-07
Yes, i tried mounting it with sudo and it worked. But again, when I tried to access the folder, it just didn't give me the access to it. Repeating the same thing as I don't have enough permission....

I checked the properties of the folder and found the folder still have "root" as the owner. I guess if we mount it with sudo, it will be regarded as mounting it with the "root" account.

---

### Post by OBnascar on 2007-02-07
> **yogasades said:**
> I checked the properties of the folder and found the folder still have "root" as the owner. I guess if we mount it with sudo, it will be regarded as mounting it with the "root" account.

To change the ownership of a directory in a terminal type:
```
sudo chown UserName /path_to_folder
```

or change all files in a folder:
```
sudo chown -R UserName.UserName ~/name of folder
```

Try that and see if it works for you.....

---

### Post by bodhi.zazen on 2007-02-07
> **OBnascar said:**
> To change the ownership of a directory in a terminal type:
```
sudo chown -R UserName.UserName ~/name of folder
```

Try that and see if it works for you.....

Good advice, but it depends on the file system. The above advice will not work with nfts or fat 32.

for ntfs : ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

for fat 32 you need to use options like uid=xxx gid=yyy umask=000

Example:

sudo mount -t vfat /dev/hdxy /mount/point -o uid=1000,gid=100,umask=007

Fstab: /dev/hdxy /mount/point vfat auto,users,uid=1000,gid=100,umask=007 0 0

For linux native file systems, first mount the partition, then use chown and chmod to change ownership and permissions.

---

### Post by OBnascar on 2007-02-07
> **bodhi.zazen said:**
> Good advice, but it depends on the file system. The above advice will not work with nfts or fat 32.for ntfs

Good point bodhi.zazen, I missed that part !

---

