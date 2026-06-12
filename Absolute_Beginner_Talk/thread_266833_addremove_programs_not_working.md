---
title: "add/remove programs not working"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Adventx on 2006-09-27
I was attempting to uninstall Alacarte Menu Editor due to the fact that it did not work and I tried a fix from another post with no luck. So when I opened add/remove programs it tried to update the list and then got an error. So I tried to do " sudo aptitude update " and this is what I got. 
```
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Get:2 http://mirror.ubuntulinux.nl dapper-seveas Release.gpg [309B]
Ign http://people.ubuntu.com ./ Release.gpg
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-security Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://mirror.ubuntulinux.nl dapper-seveas Release
Ign http://people.ubuntu.com ./ Release
Err http://mirror.ubuntulinux.nl dapper-seveas Release

Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://www.getautomatix.com dapper/main Packages
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-security Release
Ign http://people.ubuntu.com ./ Packages
Get:7 http://mirror.ubuntulinux.nl dapper-seveas Release [20.7kB]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://people.ubuntu.com ./ Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/main Sources
Ign http://mirror.ubuntulinux.nl dapper-seveas Release
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://mirror.ubuntulinux.nl dapper-seveas/extras Packages
Hit http://archive.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Get:8 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Fetched 21.0kB in 20s (1003B/s)
Reading package lists... Done
W: GPG error: http://mirror.ubuntulinux.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems

```

Ran apt-get update as it suggested and the same thing happend. Any suggestions?

---

### Post by croak77 on 2006-09-27
Try copying and pasting this in a terminal,
```

wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```

Then run sudo aptitude update

---

### Post by Adventx on 2006-09-27
now I am getting this 
```
x@x-laptop:~$ wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
--23:02:01--  http://mirror.ubuntulinux.nl/1135D466.gpg
           => `-'
Resolving mirror.ubuntulinux.nl... 82.148.208.151
Connecting to mirror.ubuntulinux.nl|82.148.208.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 757 [text/plain]

100%[====================================>] 757           --.--K/s

23:02:11 (365.97 KB/s) - `-' saved [757/757]

gpg: no ultimately trusted keys found
OK

```

---

### Post by croak77 on 2006-09-27
That's ok. Does sudo aptitude update return the same error now?

---

### Post by Adventx on 2006-09-27
now its showing 

```
Err http://mirror.ubuntulinux.nl dapper-seveas Release.gpg
  Temporary failure resolving 'mirror.ubuntulinux.nl'

```

on the last line and add/remove is still not showing any aps under any category

---

