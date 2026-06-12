---
title: "Accessing files on Macintosh HD without root"
date: 2013-03-09
forum: Apple Hardware Users
---

### Post by Hemmer on 2013-03-09
I've followed the procedure [here]("http://www.jfdesignnet.com/?p=2083") to change the UID of my ubuntu user ("hemmer", same as my mac username) to 501 sucessfully:

**On ubuntu:**
```
hemmer@hemmer-mbp:/media$ id -u hemmer
501
```

[B]Proof that mac user is also hemmer with uid 501
[/B]```
sudo ls -thorn /media/hemmer/Macintosh\ HD/Users/hemmer 
total 16M
drwxr-xr-x 1 501    5 Dec  4  2011 Public
drwxr-xr-x 1 501    2 Jun  6  2012 dwhelper
[etc]

sudo ls -thor /media/hemmer/Macintosh\ HD/Users/hemmer 
total 16M
drwxr-xr-x 1 hemmer    5 Dec  4  2011 Public
drwxr-xr-x 1 hemmer    2 Jun  6  2012 dwhelper
[etc]

```





I can navigate and see the files on my mac partition fine using: ```
 gksu nautilus
```

For reference:
 ```
mount | grep '^/dev'
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
/dev/sda1 on /boot/efi type vfat (rw)
/dev/sda2 on /media/hemmer/Macintosh HD type hfsplus (ro,nosuid,nodev,uhelper=udisks2)

```

The permissions for both /media/hemmer and /media/hemmer/Macintosh HD are both root:

```
sudo ls -thor /media/
total 4.0K
drwxr-x---+ 3 root 4.0K Mar  9 19:20 hemmer

sudo ls -thor /media/hemmer/
total 0
drwxr-xr-x 1 root 34 Mar  9 13:15 Macintosh HD
```

If I want to be able to access (read only is fine) the files on Macintosh HD without being root, do I have to change the permissions from inside Ubuntu or Mac OS? If so how? Is it safe to chown/chmod -r /media/hemmer to my username (hemmer)?

Thanks, Hemmer

---

### Post by Hemmer on 2013-03-09
Fixed: changing permissions of /media/hemmer/ worked

```
sudo chmod 775 /media/hemmer/
```

---

