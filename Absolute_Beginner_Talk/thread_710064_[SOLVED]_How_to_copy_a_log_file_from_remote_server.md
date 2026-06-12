---
title: "[SOLVED] How to copy a log file from remote server to my local machine?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-02-28
I'm logged in via ssh to a remote machine. I want to save a copy of a log file to my local machine. 

I saw this thread, but I couldn't get that method to work. Is there a simple way to copy a log file to my local machine while I am logged in to the remote machine via ssh? Thanks

---

### Post by kpkeerthi on 2008-02-28
[http://www.cisl.ucar.edu/docs/ssh/guide/node19.html](http://www.cisl.ucar.edu/docs/ssh/guide/node19.html)

---

### Post by hyper_ch on 2008-02-28
if you're on KDE you could use konqueror (or install it for gnome)... konqueror is a great file manager.

Click on the bottom taks bar with your right mouse button and split the view... then select one view and type into the address bar:

fish://USER@MACHINE

Of course replace USER and MACHINE with your actual values... then you can browse through the machine and copy the file over with drag and drop.

The other alternative would be to use SSHFS and then mount the remote computer into your local file system. You can then also easily copy the desired files.

---

### Post by justleen on 2008-02-28
scp (ssh copy)

local from remote:
```
$ scp username@host:/path/to file /destination/  
```

remote to local (when your connected over ssh to the remote)
```
scp /path/to/file username@localmachineip:/destionation/path
```

you could also install SSHFS, ssh file sytem, this will allow you to mount a drive over ssh (and then you can just drag and drop)

---

