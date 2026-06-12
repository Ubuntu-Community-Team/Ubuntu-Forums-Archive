---
title: "update problem"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-01-11
Can anyone help me with this:


I ran the update manager, and after it reads all the package information I get an error saying "could not download all repository indexes"....and when i scroll down the list of repositories that there was a problem with they all have "bad gateway" next to its IP address.

Then I tried apt-get update and I get the same problem.....

Can anyway help me out here, ive been running ubuntu for awhile now and Ive never had this problem?

---

### Post by taurus on 2007-01-11
Can you post the complete output of this command here?

```
sudo aptitude update
```

---

### Post by Loki57701 on 2007-01-11
I tried that and I still get the same "bad gatway" problem with most of the repositories

---

### Post by tomkae on 2007-01-11
I hope you won't mind my jumping in here, but I'm having the same problem;

oem@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  502 Bad Gateway [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
  502 Bad Gateway [IP: 146.137.96.7 80]
Fetched 3B in 17s (0B/s)
Reading package lists... Done
oem@ubuntu:~$

---

### Post by taurus on 2007-01-11
Just remove the **us.** from the repos in /etc/apt/sources.list and you should be fine again.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Loki57701 on 2007-01-11
thanks that worked for me....

---

### Post by taurus on 2007-01-11
> **Loki57701 said:**
> thanks that worked for me....

Glad to hear.  ;)

---

