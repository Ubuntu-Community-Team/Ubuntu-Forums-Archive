---
title: "GUI client for SCP or SFTP"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by saracen on 2006-08-11
Does anyone know of any?  I've used gftp, but that only has ssh2 and transfers are a lot slower over that protocol.  When using scp or sftp, I'm getting speeds of over 70K/sec between my 2 computers.  When i use gftp with ssh2 I get around 20K/sec.

---

### Post by colo on 2006-08-11
You could use FUSE to "mount" your sftp-accounts transparently, and then use whatever filemanager you like to manage it. There are numerous guides on the web (and these forum as well, I believe) on how to do that.

---

### Post by steve.horsley on 2006-08-11
In Nautilus, choose Tools->Connect to server. Choose SSH and fill in some other details.

---

