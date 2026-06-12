---
title: "Whats wrong with my FSTAB file?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-26
I am trying to get these network shares to mount upon boot.  This file I saved from my Ubuntu workstation while I was running 6.10.  Now that I am running 7.04 it won't work.  I haven't changed anything in the FSTAB file since the OS upgrade.


I know that the IP information is correct.  I just can't figure out why they are not mounting.  I can browse to these shares and see them fine through Nautilus and all the permissions both on the server folders and the local directories that I am trying to mount to are completely open (chmod ugo+rwx)




```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f123a09-0273-4c54-a70a-fedeaf3a5b74 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3fb016d7-f9fb-45f0-9be0-a466bb856f50 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Wdrive
//10.10.10.82/Wdrive /media/shares/Wdrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777, 0    0
#Ydrive
//10.10.10.82/Ydrive /media/shares/Ydrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777, 0    0
#Zdrive
//10.10.10.82/Zdrive /media/shares/Zdrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777, 0    0
```

---

### Post by bodhi.zazen on 2007-07-26
The only glaring problem I see is with your fmask and dmask. Do you want those to be 000 (rather then 777, 777 = permissions of 000)

Try mounting those drives (manually) from a terminal and post any errors ...

---

### Post by kc5hwb on 2007-07-26
dumb question, I know... but how do I do that manually?  I forget, its been a while..

---

### Post by bodhi.zazen on 2007-07-26
Oh, .... It may be a bug.

See here : [https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48)

And this thread as well ...

[http://ubuntuforums.org/showthread.php?t=282008](http://ubuntuforums.org/showthread.php?t=282008)

HTH

---

### Post by obrient on 2007-07-26
Thought I might share my  fstab area. Mine is a bit different in the permissions and the only other area I can see is the file system. cifs vs. smbfs

```
//192.168.1.80/Music  /mnt/MyMusic  cifs   credentials=/root/.smbcreds,ro  0 0

```

The other thought is the smbcreds file. Is it in the right format?

```
username=
password=
domain=

```

---

### Post by kc5hwb on 2007-07-29
I don't have a line for "domain" in my /root/.smbcredentials file.  But I didn't have one last time when this setup worked either.  I can certainly try and input it to see if that worked.

---

