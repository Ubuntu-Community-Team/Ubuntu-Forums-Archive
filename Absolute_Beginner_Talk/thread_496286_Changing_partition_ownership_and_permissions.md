---
title: "Changing partition ownership and permissions"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by kholdstare311 on 2007-07-08
In this tutorial here: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") it's said that I cannot have write access to my Shared FAT32 partition from my standard login account on Ubuntu, and gives an explanation on how to edit /etc/fstab to give my account permissions as well as or in place of the /root permissions.

My question is, can someone give me a better description on how to do this (his guide is on the last page of the article), or at least just help me through the whole thing? I'm a big'ole newbie to linux, so I'm sorta lost.

I just need to change ownership of my Shared FAT32 to my account rather than /root.

---

### Post by pbaumgar on 2007-07-09
> **kholdstare311 said:**
> In this tutorial here: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") it's said that I cannot have write access to my Shared FAT32 partition from my standard login account on Ubuntu, and gives an explanation on how to edit /etc/fstab to give my account permissions as well as or in place of the /root permissions.

My question is, can someone give me a better description on how to do this (his guide is on the last page of the article), or at least just help me through the whole thing? I'm a big'ole newbie to linux, so I'm sorta lost.

I just need to change ownership of my Shared FAT32 to my account rather than /root.

What is your FAT32 partition mounted as?  On the command line type:

df

Now, to see what your User ID and Group ID is, type (insert your login id where username is):

grep <username> /etc/passwd

Post the output of those two commands and then we can edit your /etc/fstab file.

---

### Post by kholdstare311 on 2007-07-09
for the shared partition it says /dev/sda7, and the other command turns up this data:

name: x:1000:1000:Kris,,,:/home/name:/bin/bash

The space between the colon and x after the first "name" is there to prevent the forum from displaying ":x"

---

### Post by bodhi.zazen on 2007-07-09
You set read-write of fat partitions at the time of mount ..., with umask

so either :

```
sudo mount -t vfat /dev/sda7 <mount_point> -o uid=1000,gid=100,umask=007
```

Or change your options in fstab (4th column)

```
gksu gedit /etc/fstab
```

Change the options to something like this :

> /dev/sda7 <mount_point> vfat auto,uid=1000,gid=100,umask=007 0 0

Then unmount and re-mount the partition.

---

### Post by pbaumgar on 2007-07-09
> **kholdstare311 said:**
> for the shared partition it says /dev/sda7, and the other command turns up this data:

name: x:1000:1000:Kris,,,:/home/name:/bin/bash

The space between the colon and x after the first "name" is there to prevent the forum from displaying ":x"

Ok, so now type:

sudo gedit /etc/fstab

Add:  uid=1000, gid=1000 to the line that has /dev/sda7 on it.  Just like the example in the article.

---

### Post by kholdstare311 on 2007-07-09
the article shows nothing like "umask=007" as is in my fstab file - should I replace this with the "uid=1000" (as it's in the place that article shows as having the UID) or should I leave it in somehow?

---

