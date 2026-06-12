---
title: "Unable to download software"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by longissor on 2006-09-09
When I try using synaptic or the Add/Remove feature I am unable to download any software because it cannot connect with the IP. My internet connection is active and I am able to surf the web, but alas it just will not work.
Any help would be greatly appreciated.

---

### Post by taurus on 2006-09-09
Open a terminal, Applications -> Accessories -> Terminal, and see what happens...

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by longissor on 2006-09-09
I tried that:


longissor@longissor-desktop:~$ sudo aptitude update
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 195.248.90.54 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.54 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
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
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 146.137.96.7 80]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
longissor@longissor-desktop:~$ sudo aptitude upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
longissor@longissor-desktop:~$

=/

---

### Post by Psquared on 2006-09-09
Make sure you don't have synaptic or adept or other update software running.

This happens to me sometimes. I just wait a while and try again. Sometimes the sources are overloaded or down for maintenance. They usually come right back up.

---

### Post by taurus on 2006-09-09
If you want to see if another one's running, you can look at this list!

```
ps -A
```

---

