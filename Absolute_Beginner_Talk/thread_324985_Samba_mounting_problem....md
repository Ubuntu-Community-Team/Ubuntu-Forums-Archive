---
title: "Samba mounting problem..."
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2006-12-24
I am trying to mount this network share on my computer. In konqueror, i can see the share and all the files, i just want to mount it (still being writable), but it just wont work.  here is the error...

```

rmorris@little:~$ sudo mount -t smbfs -o username=lxserver,password=338573,dmask=777,fmask=777 //192.168.2.10/music /home/rmorris/music/
mount: wrong fs type, bad option, bad superblock on //192.168.2.10/music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by jnet3000 on 2007-01-16
First check if you have smbclient and smbfs installed:

    dpkg-query -l "smb*"

If there is no Version, then it's not installed.

Install it like this:

    sudo apt-get install smbfs
    sudo apt-get install smbclient

Then retry mount.  Mine worked after installing them.

---

