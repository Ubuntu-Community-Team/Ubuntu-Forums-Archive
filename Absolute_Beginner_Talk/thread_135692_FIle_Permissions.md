---
title: "FIle Permissions"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by TrevorNet on 2006-02-24
Hi! :) 

I have managed to set up a "file server" across our network using Samba. So far I have 4 Win XP and 2 OS X computers talking to it. The problem is, when one of the users drops a file, creates a folder, etc... the object is locked down to that user by way of permissions. I have four user accounts, all belonging to the user group of samba. The shared drive itself "/mango" has been asigned to the group of "samba" as well. (/mango is the mount point for a second 80GB HD)

Is there anyway to set the permissions of any file that is dropped in this directory so that it will remain public read/write from the start?

My duct tape solution has been to run a chmod terminal command every so often. It's not difficult, it just takes time. As our office grows, it would become a bigger issue.

One solution would to use a single log-in for everybody, but... not what I want.

Clues? Suggestions?

Much thanks!
Trevor

---

### Post by TrevorNet on 2006-02-24
no?

(sorry for the bump, this has me major confused)

---

### Post by wylfing on 2006-02-24
Look in /etc/samba/smb.conf and find lines like this:

create mask = 0700
directory mask = 0700

Change them both to 775. This makes things a little less "secure" but it should be fine in a small office situation.

---

### Post by TrevorNet on 2006-02-24
Thank you very much!

---

### Post by dwasifar on 2006-03-16
Is there any way to accomplish the same thing for creates at the server itself?  i.e., I copy or create a folder containing files, and it automatically sets permissions to 777 or 775 without my having to chmod everything?

---

