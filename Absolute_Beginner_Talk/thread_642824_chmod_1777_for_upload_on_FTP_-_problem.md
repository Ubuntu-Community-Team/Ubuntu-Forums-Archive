---
title: "chmod 1777 for upload on FTP - problem"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by dakoth on 2007-12-17
Hiya. I've been trying to set up a local FTPd (using PureFTPd). I've been able to setup the program and have users logging in and downloading/uploading without any issues. The problem is with the permissions for files/folders.

To briefly outline the structure of the ftp:
one directory for uploads, entitled 'upload'
one directory for downloads, entitled 'download'

My own user (dak) is the owner of all directories, and the ftpgroup (that all ftp users belong to) is the group for all folders.

I've chmod'd the upload folder to 1777 (sticky is there to avoid letting one user delete another's upload). The issue here becomes that I (as dak) can't move or delete stuff that another user uploads. I have to superuser in order to admin my own ftp. Kinda annoying.

Is there a way around this issue? I would like to allow users to delete their own uploads in case they make a mistake, but I would still like to handle the files/folders without having to go SU.

---

### Post by Severun on 2007-12-17
Have you tried this?

chown dak ftpdir
chgrp ftpgroup ftpdir
chmod 1770 ftpdir

That's a bit more secure than 777 (shudder).

---

### Post by dakoth on 2007-12-18
It certainly does, but that doesn't change my initial problem I'm afraid.

Oddly enough, I've found that if I upload something with one user, I am able to move it with my user without SU'ing if I do so before anyone else attempts to change it.

For example, if I upload something with user A, and then attempt to delete it with user B, it becomes un-editable, and I have to move/delete it with SU.

If I on the other hand never touch it with user B after I upload it with user A, I am able to move/delete it without using SU.

I suppose that's how 'sticky' works? I'm rather new to the concept. Oh well, it makes the problem smaller, since people will generally only attempt to delete other people's uploads by mistake.

---

