---
title: "File Sharing between Ubuntu and Windows"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Rob2Kx on 2007-05-06
Hi,

I want to share some files over a 2 computer network.  The other computer runs Windows XP.  I set the folder that I want to share as shared.  However, when I try to access the Ubuntu computer from the Windows computer, it asks for a user name and password.  I didn't set a username or password for the shared folder.  I tried using my Ubuntu username and password but that didn't work... any ideas?

Thanks!

---

### Post by brennydoogles on 2007-05-06
> **Rob2Kx said:**
> Hi,

I want to share some files over a 2 computer network.  The other computer runs Windows XP.  I set the folder that I want to share as shared.  However, when I try to access the Ubuntu computer from the Windows computer, it asks for a user name and password.  I didn't set a username or password for the shared folder.  I tried using my Ubuntu username and password but that didn't work... any ideas?

Thanks!

This is a guess, but try making another user in Ubuntu called windows or something clever like that, and make sure it has permission to access the files you want to share and try logging in that way. You will also have to make sure that windows is able to read the file system that your linux uses, because by default windows can't recognize that ext2 or ext3 exist. If that doesn't work I would try Samba.

---

### Post by raja on 2007-05-06
[This thread]("http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder") discusses the same problem and a couple of fixes.

---

### Post by Nythain on 2007-05-06
you need to set your samba security to share and not user... you can manually edit yoru /etc/samba/smb.conf there are many helpfull guides and tutorials for this, just search the forums and google for samba

---

