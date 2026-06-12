---
title: "Mount Windows Share"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by broth420 on 2007-07-01
I am trying to mount a windows share 
here is the information

windows username:  user
windows password:  canttell
workgroup name:  homenetwork (I don't know if this is needed)
IP address of windows server:  192.168.0.10
Share to access:  mp3
ubuntu username:  user

I created the folder /mnt/mp3

I tried the following command and the message after is what I got.

user@MEDIA-SERVER:~$ sudo mount -t smbfs -o username=user,password=canttell,uid=user \ //192.168.0.10/mp3 /mnt/mp3
mount: wrong fs type, bad option, bad superblock on  //192.168.0.10/mp3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What did I do wrong?  I pulled this right out of the Ubuntu Linux Bible.  
Another question....is the share name case sensitive, and if so, should I follow the windows convention?

---

### Post by broth420 on 2007-07-01
I figured it out (it was pretty stupid), but if anyone else wants to know)

sudo mount -t smbfs -0 username=user,password=psswd //IP_Address/share /mnt/share

/mnt/share (or whatever you use) must already be created.

There may be some permissions to set as well.  Just for good measure I set...

sudo chmod 0777 /mnt/share

I don't know about the permissions, but my mount works just fine.

Also, you may have to install the package for smb file system, and if so...
sudo apt-get install smbfs

---

