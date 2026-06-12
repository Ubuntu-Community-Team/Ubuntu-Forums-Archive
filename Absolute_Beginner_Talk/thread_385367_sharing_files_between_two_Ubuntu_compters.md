---
title: "sharing files between two Ubuntu compters"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by goodmanbrown on 2007-03-15
I would like to browse and copy files from my desktop to my new laptop, both of which run Ubuntu.  What is the recommended way of doing this in an all-Linux environment?  I used Samba for file-sharing with roommates years ago, but that is specifically for networks with Windows boxes, right?

---

### Post by floke on 2007-03-15
Yes, you can use NFS for Linux to Linux sharing - its very easy.

See here: [http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)
And here: [http://nfs.sourceforge.net/nfs-howto/ar01s03.html](http://nfs.sourceforge.net/nfs-howto/ar01s03.html)

Good luck

---

### Post by steve.horsley on 2007-03-15
Another opption that is simple to set up is an SSH server. Install package openssh-server on one machine, adn from the other, in nautilus, File->Connect to server, choose type SSH. Bang in the IP address and username and click connect.

---

### Post by goodmanbrown on 2007-03-15
Perfect!  Thank you.

---

### Post by goodmanbrown on 2007-03-15
Oh, how cool that Nautilus does this!  I already have an ssh server running on my desktop, so my work is done before it ever began.

---

