---
title: "Transferring files over the internet"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-12-06
How can I give a remote user access to a folder with my hard drive for the purposes of large file transfers?  Can this be done by setting up an FTP of sorts?

---

### Post by Dr Small on 2007-12-06
You do this with FTP or SSH, as it is possible with both.

---

### Post by dreadh3ad on 2007-12-06
I really need to restrict the user to only access 2 folders.  Can you point me in the direction of a tutorial?

---

### Post by ectospasm on 2007-12-06
There are many ways of doing this, including scp (ssh), WebDAV, ftp, etc.  The simplest to set up would be scp/ssh, since you probably already have OpenSSH installed and set up.  You'd need to give this user a non-privileged account on your system, and set their home directory to be where you want them to put the files.  The most difficult part of this would be the client they use to connect.  If they're using a Windows machine, [WinSCP]("http://http://winscp.net/eng/download.php") should be enough.  If they're using a UNIX variant, they should be able to use scp (part of the OpenSSH client package).  

HTH

---

### Post by ectospasm on 2007-12-06
> **dreadh3ad said:**
> I really need to restrict the user to only access 2 folders.  Can you point me in the direction of a tutorial?



Just use SSH/SCP, and only give the user write access to the two folders you need them to.

---

