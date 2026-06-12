---
title: "Interesting Permissions Problem"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-07-15
Im making an ftp server for use by myself and family, so I want a few folders restricted. I did this by 'chown root'. Now my torrent program doesnt download files to the directory. Would I just need to locate the torrent directory (ktorrent in this case) and change the owner on that to root as well?

---

### Post by starsky on 2007-07-15
> **Daergeth said:**
> Im making an ftp server for use by myself and family, so I want a few folders restricted. I did this by 'chown root'. Now my torrent program doesnt download files to the directory. Would I just need to locate the torrent directory (ktorrent in this case) and change the owner on that to root as well?


The directory is owned by the super user or a user called "root". Hence, when your torrent software starts to write to that directory, it can't because the torrent software is started by normal user (YOU). 

Now the solution
go to that directory of yours and type these 
```

$ sudo chown YOUR_USERNAME:YOUR_USERNAME THE_DIRECTORY_YOU_WANT_TO_WRITE

```

for e.g.,
```

$ sudo chown starsky:starsky ubuntu_iso_torrent

```


then load the torrent software as normal user :)

post back if any trouble

HTH

---

### Post by Daergeth on 2007-07-15
Ktorrent now works, but this just sets my directory back to normal user mode, yes? 

Ths is how the directory is setup, /home/xfce/Files/Ktorrent

had " Files" restricted to root, but obviously ktorrent couldnt download to its dowload folder (ktorrent)

---

### Post by starsky on 2007-07-15
sorry i don't understand a word you said. :P
do you mean your ktorrent CAN write to /home/xfce/Files/Ktorrent/ ?

---

### Post by Daergeth on 2007-07-15
Heh, well it can now that I set the owner back to me and not root. But Im trying to get ktorrent to download files into a root owned file. Sorry if this sounds confusing, hard to describe the issue at hand :D

---

### Post by freebird54 on 2007-07-15
It is not accessible to any other use than you (and root) by default.  If someone has your normal user password, they also have your root access as well anyway!

So - further protection... create new user with new password, and operate things as THAT user...(can be simultaneous with yourself if desired).  OR

encrypt the directory that you wish protected, and unhide it when in use only.  To do that use [THIS](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/).

A couple of possible solutions - depending on what the problem actually is  :)

---

### Post by starsky on 2007-07-15
> **Daergeth said:**
> Heh, well it can now that I set the owner back to me and not root. But Im trying to get ktorrent to download files into a root owned file. Sorry if this sounds confusing, hard to describe the issue at hand :D

well, if you are talking about that partially downloaded file OWNED by root, then do this.

Close ktorrent.

```

$ sudo chown YOU:YOU PARTIALLY_DOWNLOADED_FILE

```

restart ktorrent. now that partially downloaded file should be accessible by ktorrent.

HTH

---

