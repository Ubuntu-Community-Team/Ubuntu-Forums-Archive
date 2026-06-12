---
title: "making mount point user accessible"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-19
Hello,

apart from swap and / and I have two additional partitions for documents and stuff which I would like to mount at /home/cruz/documents and /home/cruz/stuff. Well I managed the mounting part but the problem is that the directories of the mount points (documents and stuff) are owned by root and writable only by root. How can I accomplish mounting those partitions exactly where I wanted but having the directories owned or at least writable by "cruz"?

Thanks
Cruz

---

### Post by crokett on 2006-09-19
google or man pages for chmod and chgrp. I also suggest reading on permissions in Linux in general

---

### Post by aysiu on 2006-09-19
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Cruz on 2006-09-19
Man I'm so stupid. I know about chown and chmod but I supposed that root is mounting the partitions and thus the mount points are owned by root. 

Is it possible to delete this thread? :)

---

### Post by Brunellus on 2006-09-19
also.  nothing stops you from simply creating a mount point in your home directory and mounting the device to *that* part of the filesystem.  You'd still need root access, or at least enoug privileges to mount that device, but the user would own the mount point.

---

### Post by Skip Da Shu on 2007-11-12
> **Brunellus said:**
> also.  nothing stops you from simply creating a mount point in your home directory and mounting the device to *that* part of the filesystem.  You'd still need root access, or at least enoug privileges to mount that device, but the user would own the mount point.
Glad u didn't delete the thread because this is what I'm trying to do now with smbmount...

---

