---
title: "Disk usage question df -h"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by bowens44 on 2007-11-25
Can someone please explain what I am seeing here? I have gutsy installed on a 250gig drive, I was expecting to see something similar to what I see at the bottom for the network shares. 

thanks


user:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun               1014M  260K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   60K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
//192.168.5.100/linux_bkups
                      153G   73G   81G  48% /media/backups
//192.168.5.100/MP3   153G   73G   81G  48% /media/mp3s
//192.168.5.100/data   38G   32G  6.1G  84% /media/data
root@network23:~# df -ah

---

### Post by forestpixie on 2007-11-25
not too sure what you mean , I do see something similar;)

---

### Post by Keith Hedger on 2007-11-25
Seems fairly self explanatory to me, but if you want details of the df command use man df

---

### Post by bowens44 on 2007-11-25
> **Keith Hedger said:**
> Seems fairly self explanatory to me, but if you want details of the df command use man df

I did read the man page before posting. To me, this isn't self explanatory, thus my post. I did post in absolute beginner talk because of the basic nature of my question. If you would explain this self explanatory information, I would greatly appreciate it.

I see disk usage info about my network drives , that info IS self explanatory but the info about the drive on which I have installed the Linux distro is meaningless to me.

---

### Post by geirha on 2007-11-25
It's odd that your / partition doesn't show. what does ```
df -h /
``` say? If you specify a path behind the df command, it will only show an entry for the filesystem that directory or file is located.

---

### Post by bowens44 on 2007-11-25
> **geirha said:**
> It's odd that your / partition doesn't show. what does ```
df -h /
``` say? If you specify a path behind the df command, it will only show an entry for the filesystem that directory or file is located.

That shows something more along the lines of hat I expected to see.

:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
-                     224G  4.5G  208G   3% /

The reason that I'm concerned is that on other distros that I use, namely Fedora 8 and Slackware 10 ,  I always see the available and used disk space like I do with the above command.

---

### Post by MatthewMetzger on 2007-12-07
I'm concerned too. I just upgraded to gutsy from dapper (aptitude dist-upgrade through each release). On dapper, I'd run df -h and it would give me the information about all mounted volumes including my two RAID 1 arrays put together as a LVM volume.

I now see none that when running df -h. Here's what I get:

Filesystem            Size  Used Avail Use% Mounted on
varrun                506M  176K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M   27M  480M   6% /dev
devshm                506M     0  506M   0% /dev/shm


My big volumes are not showing up!

---

### Post by qix on 2007-12-07
I find it rather strange aswell, that all of your mounts aren't showing up.

I don't really know what can solve it, but try:
```
sudo df -h
df -ah
```

An ugly solution is to do a 
```
mount
```
and then find the relevant mounts and supply them manually to df, eg if you have a partition mounted on /home, you can do a
```
df -h /home
```
and get the info about that specific mount.

---

