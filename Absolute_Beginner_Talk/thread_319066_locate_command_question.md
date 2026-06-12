---
title: "locate command question"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-12-15
I have been wrestling with trying to install Bugzilla on Ubuntu LAMP server.  Using apt-get the first time, it worked, but I needed the latest stable version so used apt to remove bugzilla, but it never really removed it... I used the -Purge command to get rid of config files... but bugzillla was still here and there throughout the system.  I finally just went in and removed these directoires... well, maybe not all of them, I am too used to the Windows way, dumping all of an application in one directory so I am not to aware of all the different locals Ubuntu distributed Bugzilla... anyway, even after deleting these directories, if I issue the locate command again, all the directories that have been removed still appear.  But they are not there, if I attempt to navigate to them, I get no where.  I am using Putty to ssh into the server.  I am left wondering if these files are still there or not?? How do I exercise these 'ghosts' from the machine??
thanks

---

### Post by scxtt on 2006-12-15
**updatedb** will make locate give you truer results ...

---

### Post by kpm on 2006-12-15
> **scxtt said:**
> **updatedb** will make locate give you truer results ...

Thanks!

---

### Post by szf on 2006-12-15
If memory serves, locate is now a synonym for slocate. And slocate, by definition, will:
"Secure Locate provides a secure way to index and quickly search for  files on your system. It uses incremental encoding just like GNU locate to compress its database to make searching faster, but it will also store file permissions and ownership so that users will not see files they do not have access to." source: [linux.about.com]("http://linux.about.com/library/cmd/blcmdl1_slocate.htm")

So you may not see *all* - depending on invokation.

---

### Post by scxtt on 2006-12-15
just sudo it ;)

---

