---
title: "network permissions on remote files"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2007-03-07
I've sneakily installed Ubuntu at work, and I have to say it's brilliant!  We use linux servers and it's much easier to connect to them (with XDCMP) than with windows!

However, one question - is there any way to have the permissions on network files be the same on my machine as on the server?  To clarify: I can copy some files to my network server filespace, using samba from a local login, and modify the permissions for users of my machine (ie me).  If I want to edit the file permissions, so that people on other machines can access the files on the server, I have to login through XDCMP and change the permissions there.  Is there anyway to change the remote permissions from a local login session?

If I do ```
chmod o=rwx *filename*
``` all users on my machine can access the files, but other users on the network cannot - I have to do the same command from an XDCMP session to make this work.

---

