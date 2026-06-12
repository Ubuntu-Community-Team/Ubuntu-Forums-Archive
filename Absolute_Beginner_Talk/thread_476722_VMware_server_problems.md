---
title: "VMware server problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by TigerTail on 2007-06-17
I cant uninstall it im having problems with it and i just dont want it anymore. I intalled it using Automatix2 and I try to uninstall it using the same program but it wont uninstall how can i manually remove it?

---

### Post by dreadlord_chris on 2007-06-17
> **TigerTail said:**
> I cant uninstall it im having problems with it and i just dont want it anymore. I intalled it using Automatix2 and I try to uninstall it using the same program but it wont uninstall how can i manually remove it?

```

sudo apt-get remove vmware-server

```

does that give you any errors? What are they?

---

### Post by TigerTail on 2007-06-17
this is what i get:


brandon@brandon-desktop:~$ sudo apt-get remove vmware-server
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 131MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106797 files and directories currently installed.)
Removing vmware-server ...
dpkg - warning: while removing vmware-server, directory `/etc/vmware/ssl' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/etc/vmware' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/lib/vmware-server/Virtual Machines' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/lib/vmware-server' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/run/vmware' not empty so not removed.
brandon@brandon-desktop:~$

---

### Post by TigerTail on 2007-06-17
theres only a couple programs that i need to run. Is Wine pretty good for that?

but first i want to get rid of vmware i made a big partition with it and i need the space

---

### Post by TigerTail on 2007-06-17
ok this is what i need to do everyone. the only software must for me is a basic good torrent downloading program all the ones ive tried for ubuntu werent able to pause the download so i couldnt shut off my computer or let other ppl log into my computer or else i would have to start over on my download!!

so now i have vmware on my computer and i cant get rid of it. i need it gone and a good torrent downloader that has the basic feature of resume on it. and a good video player that supports all different formats. i have vlc and yes ive downloaded all the plugins for movie player but half of my videos show a black screen with sound arrrrghhh. but yeah i just need vmware off and i will try to go from there

---

### Post by dreadlord_chris on 2007-06-18
> **TigerTail said:**
> this is what i get:


brandon@brandon-desktop:~$ sudo apt-get remove vmware-server
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 131MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106797 files and directories currently installed.)
Removing vmware-server ...
dpkg - warning: while removing vmware-server, directory `/etc/vmware/ssl' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/etc/vmware' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/lib/vmware-server/Virtual Machines' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/lib/vmware-server' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/run/vmware' not empty so not removed.
brandon@brandon-desktop:~$

Ok... so that worked. Vmware-server is now uninstalled. Those warning are jst telling you that it left some files behind - you don't want/need them anymore, then get rid of them:
```

gksudo nautilus

```
That will open your file manager with *root* privileges - go to the folders and delete them...

---

### Post by dreadlord_chris on 2007-06-18
> **TigerTail said:**
> ok this is what i need to do everyone. the only software must for me is a basic good torrent downloading program all the ones ive tried for ubuntu werent able to pause the download so i couldnt shut off my computer or let other ppl log into my computer or else i would have to start over on my download!!

so now i have vmware on my computer and i cant get rid of it. i need it gone and a good torrent downloader that has the basic feature of resume on it. and a good video player that supports all different formats. i have vlc and yes ive downloaded all the plugins for movie player but half of my videos show a black screen with sound arrrrghhh. but yeah i just need vmware off and i will try to go from there

uh... like I said - you actually did uninstall vmware....

Anyway, I use ktorrent - it's in the repositories. I've never had any major problems with it. I've paused, rebooted in the middle of transfers, had the computer crash/freeze while torrents were running - and have always been able to resume transfers without having to restart. Also, it's got a pretty good torrent search function built in.

As for your video problems - what kind of videos are not working? Also - did you install the w32codec package?

---

### Post by mooscape on 2007-06-19
Even with uninstall-vmware you will have to manually uninstall all the packages of vmware to get rid of it.   If you have the time, try reinstalling vmware afresh, it is a very good program.

---

