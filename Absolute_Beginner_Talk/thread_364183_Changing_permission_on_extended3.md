---
title: "Changing permission on extended3"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by dustyhawk on 2007-02-17
filesystem is on Read for owner,group,others.  Extended 3 filesystem.

I am unable to set it to write and execute for all. Stating that "the permissions could not be changed"

this is a new ubuntu-dapper installation, wiping out an old ntfs system.. thus running on Extended3 file sys.

would like to know how to change it.  new user here as well.

---

### Post by aysiu on 2007-02-17
Is this an additional drive?

If it's the one you're using, I would highly recommend *against* changing permissions and ownership on files unless they are your own personal files (documents, pictures, music, videos, etc.).

If it's an external drive or another partition, this should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by dustyhawk on 2007-02-18
this is not an additional drive

it's the one and only drive on this laptop, which was formerly on windows xp (ntfst filesys). using the ubuntu cd, I installed ubuntu on it.  During the process i use the delete partition and now the filesys is on extended3.

i hope this information helps

---

### Post by aysiu on 2007-02-18
Then don't change permissions or ownership on anything unless they are documents, pictures, music, videos, or other personal files.

Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by dustyhawk on 2007-02-18
ok. so even if i dont change it, will i be still be able to install items? for im having issues installing firefox2-linux build, stating that i do not have permissions to do so.

---

### Post by aysiu on 2007-02-18
> **dustyhawk said:**
> ok. so even if i dont change it, will i be still be able to install items? for im having issues installing firefox2-linux build, stating that i do not have permissions to do so.
Use this:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

For generic software, this will help:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by dustyhawk on 2007-02-18
i just tries the pscyhocat firefox install instruction. using the terminal, this is what i got :


serge@UltraSoul-II:~$ sudo aptitude update && sudo aptitude install firefox
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:6 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/main Packages [13.6kB]
99% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/main Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 19s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

is this what it suppose to do ?

---

### Post by aysiu on 2007-02-18
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), **is another process using it?**
``` If you have Synaptic, Adept, or Add/Remove open, you cannot also install using *apt-get* or *aptitude* (which the script does use).

Only one program can access package management at a time. Close any other software installation programs first. Then run the script.

---

### Post by dustyhawk on 2007-02-18
ok i understand what you meant. now a noob question how do i or where do i "Close any other software installation programs".

---

### Post by aysiu on 2007-02-18
Do you have any windows open? Click the X button in the top-right corner to close the window.

You should know if you've launched Synaptic, Adept, or Add/Remove Programs. Those programs don't open in the background.

Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by dustyhawk on 2007-02-19
well if that's the case, then this is weird for the only items open is firefox and the terminal.


on a side note, my add/remove program function is now missing.

---

