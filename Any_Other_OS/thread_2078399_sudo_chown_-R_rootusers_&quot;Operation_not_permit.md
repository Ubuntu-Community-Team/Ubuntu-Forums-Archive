---
title: "sudo chown -R root:users &quot;Operation not permitted&quot;"
date: 2012-10-30
forum: Any Other OS
---

### Post by n1ght28 on 2012-10-30
on raspberry pi os XBian 0.82

using this guide [http://elinux.org/R-Pi_NAS](http://elinux.org/R-Pi_NAS)
to setup Samba share

changing the permissions of the share
```
sudo chown -R root:users /home/shares/public
```

gives me lots and lots of
```
chown: changing ownership of `/home/shares/public/': Operation not permitted
```
and all the files and folders in it.

the share is the mountpoint for my usb hardrive FAT32

where am i going wrong here???

---

### Post by oldfred on 2012-10-31
Unless you have a group users, I do not think you can use that command. 

But it will never work on FAT32 or NTFS as Windows formatted partitions do not support ownership nor permissions.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by n1ght28 on 2012-10-31
Ok,
Got it to mount with write permissions using,

```
sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000,rw /dev/sda1 /home/shares/public/disk1
```

I can create folders from the raspberry and "cd" into them,

But I cant create folders from connected Samba clients,

think its a problem with my fstab or my smb.conf

Fstab


```
//192.168.1.19/public /media/pi cifs uid=calbert,credentials=/home/calbert/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```


smb.conf

```
####### Authentication #######

security = user
  client lanman auth = Yes
  lanman auth = Yes


[global]
workgroup = WORKGROUP
netbios name = xbian
server string = xbian
log file = /var/log/samba/log.%m
max log size = 50
map to guest = bad user
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
dns proxy = no


[public]
path = /home/shares/public
public = yes
only guest = yes
writable = yes
```

where am I going wrong,

---

### Post by oldfred on 2012-10-31
I gave up on Samba a while back and use NFS. As I understand it there are two ways to do it and you cannot mix them.

Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)
See posts by Morbius1
[http://ubuntuforums.org/showthread.php?t=1649380](http://ubuntuforums.org/showthread.php?t=1649380)
[http://ubuntuforums.org/showthread.php?t=1872904](http://ubuntuforums.org/showthread.php?t=1872904)

 HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
For definitive explanation of SMB (CIFS) and how it works, see here .
[http://ubiqx.org/cifs/SMB.html](http://ubiqx.org/cifs/SMB.html)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you want to use "Classic" samba you need to go into nautilus and "unshare" Public.
If you want to stay with nautilus share you need to remove:
Quote:
[Public1]
path = /home/<user>/Public
read only = No
guest ok = Yes 

Do a ls -dl /home/<user>/Public to see if somehow nautilus-share didn't reset the permissions properly.

---

