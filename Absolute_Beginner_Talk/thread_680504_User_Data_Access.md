---
title: "User Data Access"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by expatCM on 2008-01-28
In order to make it easier keep data backed up I want to change the settings  so that each user saves their work in their own directory on the server.  

I think the way to allow the directory access is to simply add the directory / path to the fstab.

But what I want to know is how to allow a user to log on at any machine on the network so that they then transparently access the data in the server directory?  (my reasoning being that the fstab is static to a machine and mounting all directories will do nothing for security / privacy)

---

### Post by mattismyname on 2008-01-28
You'll want to set up your server as an NFS server and have it export /home to all clients.  You'll also probably want a NIS service to keep all user accounts on all clients in sync.

---

### Post by bodhi.zazen on 2008-01-28
Here is a similar thread :

[http://ubuntuforums.org/showthread.php?&t=268463](http://ubuntuforums.org/showthread.php?&t=268463)

---

