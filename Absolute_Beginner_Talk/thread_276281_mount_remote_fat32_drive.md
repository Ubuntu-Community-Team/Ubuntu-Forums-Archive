---
title: "mount remote fat32 drive"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by eXidos on 2006-10-12
My music server is on a windows media center system all I want to do is mount that drive on my ubuntu system so I can listen to music on my other linux systemsI went through all the "mount ntfs network drive" steps but Im getting this error:

exidos@EXBOX:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.1.102/media/Music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



My fstab looks like this:

//192.168.1.102/media/music    /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

what am I doing wrong?

---

### Post by echo $USER on 2006-10-12
Try this first and see if it works...

Press ALT+F2 (run app) and enter...

smb://192.168.1.102/media/music

See if it pulls up the windows share.  If it does, enter this into fstab...

> //192.168.1.102/media/music /media/music smbfs defaults 0 0

then, sudo mount -a

---

### Post by eXidos on 2006-10-12
Yes it runs but with:

smb://192.168.1.102/media/Music

just as i have it entered in my fstab

---

### Post by eXidos on 2006-10-12
no when I used 

//192.168.1.102/media/music /media/music smbfs defaults 0 0 

still same error:

exidos@EXBOX:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.1.102/media/Music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by echo $USER on 2006-10-12
> **eXidos said:**
> no when I used //192.168.1.102/media/music /media/music smbfs defaults 0 0 still same error

Change smbfs to vfat and see if it works.

---

### Post by eXidos on 2006-10-12
changed to vfat now returns this error:

exidos@EXBOX:~$ sudo mount -a
mount: special device //192.168.1.102/media/Music does not exist

---

### Post by echo $USER on 2006-10-12
> **eXidos said:**
> changed to vfat now returns this error:

exidos@EXBOX:~$ sudo mount -a
mount: special device //192.168.1.102/media/Music does not exist

I'll have to wait till i get home to help resolve this as I am at work now.  I have a book on samba at home; the answer will be in there.

---

### Post by eXidos on 2006-10-12
thanks alot that would be great!

---

### Post by eXidos on 2006-10-17
got it this is sooo n00bish 

step 1:

**sudo apt-get install smbfs**

step 2:

**sudo mkdir /media/music**
then:
**sudo chmod 0777 /media/music**

step 3:

**sudo gedit /etc/fstab**

step 4:

**//media_1/media /media/music smbfs noauto,username=admin,password=admin,uid=0,gid=500 0 0**

(I "noauto" it incase the puter is not on when mine boots "auto" if ya want it to)

step 5:

because i noauto use this to manually mount

**sudo mount /media/music**

DONE! Load your music into your fav player and go!

GOD BLESS MAN FILES!!!!

---

