---
title: "linux network shares"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by 2340newbie on 2006-12-05
being new to this OS i am trying to get 2 edubuntu computers to see each other, where do i start? i have been looking on the net but am getting confused with the array of info

---

### Post by IYY on 2006-12-05
NFS is the easiest way of sharing. Here is a tutorial to show you the command-line way of doing things (I find it easier, because it's very step-by-step:

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

If you want to use SAMBA instead (a method that allows sharing with Windows as well as Linux machines), or just like a graphical way of configuring NFS, use this tool:

System > Administration > Shared Folders

This allows you to share folders on your system, using either SAMBA or NFS. To connect to a server, you can use 

Places > Network Servers

---

