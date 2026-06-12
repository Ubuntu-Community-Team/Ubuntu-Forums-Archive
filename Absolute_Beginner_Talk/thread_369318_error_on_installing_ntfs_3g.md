---
title: "error on installing ntfs 3g"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by webofunni on 2007-02-24
after installing ntfs-3g i got all my icons of ntfs partition mounted from my desktop but still they are in /media/sdx . I can read and write data from those partitions but i dont know how to make those icons appear again in my desktop also after installing ntfs-3g when ever i try to install any package i am getting a error after installing those packages.

there is no problem in installing other packages but after installation my package manager shows following error

E: fuse-utils: subprocess post-installation script returned error exit status 1
E: ntfs-3g: dependency problems - leaving unconfigured
E: ntfs-config: dependency problems - leaving unconfigured

please help me

---

### Post by givré on 2007-02-24
webofunni, i reply to you on the ntfs-3g forum, didn't see that you also post a thread here, so i"ll copy/paste my reply :

> This is definitely not an ntfs-3g or an ntfs-config problem, but a fuse installation problem, so you should complain to the maintainer (might be me, will see) of the fuse package instead. But since i'm in good mod, i'll try to solve your problem.

First, do you use debian or ubuntu (or any derivative). Do you use third party repo to get fuse & ntfs-3g ?
Second, can i get the full output of your installation.


---

