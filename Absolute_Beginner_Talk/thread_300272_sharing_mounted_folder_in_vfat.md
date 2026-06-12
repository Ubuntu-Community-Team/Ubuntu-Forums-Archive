---
title: "sharing mounted folder in vfat"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2006-11-15
Hi,
Can anyone help me to share the folder from /media/hdb5/share
/media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
I try with this , but it does't work.

security = share

[share]
  comment = Test share
  path = /media/hdb5/boot
  public = yes
  writable = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

10x

---

### Post by taurus on 2006-11-15
Here you go...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jordanmthomas on 2006-11-15
I believe he already has it mounted, but is wanting to share it over samba.

Is this correct?

Also, does the directory /media/hd5/boot exist?

---

### Post by timon_tg on 2006-11-15
yes, /hdb5 is mounted in /media and /media/hdb5/boot exist.
I just want to share it.

---

### Post by taurus on 2006-11-15
> **timon_tg said:**
> yes, /hdb5 is mounted in /media and /media/hdb5/boot exist.
I just want to share it.
You just want to share it with other users on the same machine or people on your network!!!

---

### Post by timon_tg on 2006-11-15
with people on your network

---

### Post by timon_tg on 2006-11-16
any suggestions?

---

### Post by jaboua on 2006-11-16
umask=007

AFAIK that will give:

the owner 7-0 = 7 = 1 + 2 + 4 = execute + write + read permissions
the group 7-0 = 7 = 1 + 2 + 4 = execute + write + read permissions
everyone else 7-7 = 0 = no access at all

Remember that the umask is subtracted from 777 to give the final permissions... I would suggest that you try using umask=003 instead, that would give full permissions to owner and group and read access (7-3 = 4 = read permissions) to everyone else.

---

### Post by jordanmthomas on 2006-11-16
If you just want anyone to be able to share, here's how mine used to be set up.

```
[upload]
force user = jordan
force group = users
case sensitive = no
guest ok = yes
msdfs proxy = no
read only = no
path = /home/jordan/upload
```
for giving **everyone** on your network write permissions
```

[Desktop]
force user = jordan
force group = users
case sensitive = no
guest ok = yes
msdfs proxy = no
comment = random grab bag
path = /home/jordan/Desktop
```
For sharing and no writing.

These don't work for me in Fedora, but they did in Ubuntu.  Maybe you can use them, substituting relevant values, until you get everything sorted out.

---

### Post by timon_tg on 2006-11-17
jordanmthomas ok , but 
I want to share folder NOT in the Home directory of some Unix user, but a folder in mounted HDD (/dev/hdb5), and all Win user to be able to browse it.

---

### Post by jordanmthomas on 2006-11-17
Then change the path appropriately.
to something like /media/hdb5/*sharedfolder*

---

### Post by Yfrwlf on 2007-10-21
> **timon_tg said:**
> jordanmthomas ok , but 
I want to share folder NOT in the Home directory of some Unix user, but a folder in mounted HDD (/dev/hdb5), and all Win user to be able to browse it.

I'm not sure about this yet and am in the process of learning, but perhaps the issue you are having is one of user or group permissions?  The other possability is there is an option in smb.conf that needs to be changed to give access to places other than your home directory.

I'm in the process of trying to figure out this puzzle right now on this thread so that hopefully allowing non-home-shares will be possible in the future, or someone will be able to tell us how to do it until it is.  [http://ubuntuforums.org/showthread.php?t=585813](http://ubuntuforums.org/showthread.php?t=585813)

---

### Post by Yfrwlf on 2007-10-21
> **jordanmthomas said:**
> Then change the path appropriately.
to something like /media/hdb5/*sharedfolder*

I believe the problem they may have been describing is that things in /home are shareable, while things in /media are not.  Trying to figure out why myself...

---

### Post by Yfrwlf on 2007-10-22
Never mind, sharing mounted stuff in /media works fine now in Gutsy at least.

---

