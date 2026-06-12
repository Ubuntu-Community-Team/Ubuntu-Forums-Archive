---
title: "Add/remove program fails"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by insigniahosting on 2007-02-11
anytime i try to add or remove a program with add/remove program it fails, and i cant do anything i want to with it

---

### Post by taurus on 2007-02-11
What happens when you try it from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install **program_name**
```

---

### Post by insigniahosting on 2007-02-11
joey@joey-desktop:~$ sudo aptitude update
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 195.248.90.35 80]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache

_______________________________________________________________________________________
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by taurus on 2007-02-11
Edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all the repos.  Save it and then run

```

sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install **program_name**
```

---

### Post by insigniahosting on 2007-02-11
the box it came up with came up empty, where can i get a source list then?

( this came up in terminal)

> (gedit:6793): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


---

### Post by taurus on 2007-02-11
Use the text editor then.

Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
sudo nano -w /etc/apt/sources.list
```
Use your arrow keys to navigate and delete it with the Backspace.  Save it by holding down <Ctrl> while pressing x.  Then, answer the question with Y and Return.

---

### Post by insigniahosting on 2007-02-11
[ Error writing /etcc/apt/sources.list: No such file or directory ]

---

### Post by taurus on 2007-02-11
> **insigniahosting said:**
> [ Error writing /etcc/apt/sources.list: No such file or directory ]

Got an extra c in there.

```
sudo nano -w /etc/apt/sources.list
```

---

### Post by insigniahosting on 2007-02-11
ok i took all the us. out of all the links and saved it, add/remove still does not work

heres what i see

[http://www.insigniahosting.com/linux/Screenshot-1.png](http://www.insigniahosting.com/linux/Screenshot-1.png)
[http://www.insigniahosting.com/linux/Screenshot-2.png](http://www.insigniahosting.com/linux/Screenshot-2.png)
[http://www.insigniahosting.com/linux/Screenshot-3.png](http://www.insigniahosting.com/linux/Screenshot-3.png)
[http://www.insigniahosting.com/linux/Screenshot-4.png](http://www.insigniahosting.com/linux/Screenshot-4.png)
[http://www.insigniahosting.com/linux/Screenshot.png](http://www.insigniahosting.com/linux/Screenshot.png)

---

### Post by taurus on 2007-02-11
Run these two commands from a terminal and post any error message.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by insigniahosting on 2007-02-11
joey@joey-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 195.248.90.35 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 195.248.90.35 80]
Reading package lists... Done
joey@joey-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the gftp-common package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
joey@joey-desktop:~$

---

### Post by insigniahosting on 2007-02-28
also Kubuntu ( i made a duel boot) does something similar,

ubuntu and kbuntu both couldent locate sec, updates or something during installs

---

