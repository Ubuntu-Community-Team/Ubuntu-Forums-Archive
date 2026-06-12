---
title: "Using &quot;apt-get&quot; won't find packages"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by grimsanta on 2006-11-02
No matter what I try and download, whether it be java, or alien, it doesn't work.  It says the package isn't found, what do I do here?  I'm lost.

---

### Post by %hMa@?b&lt;C on 2006-11-02
what happens when you try 
sudo apt-get update 
or
sudo aptitude update

also what is your sources.list file?

---

### Post by ewl1217 on 2006-11-02
What would be most helpful here would be the **exact** output you get when you try to install packages. Also, as jeffc313 mentioned, the contents of the file /etc/apt/sources.list may be useful. Without knowing either of these, there isn't much we can do to help.

---

### Post by dbott67 on 2006-11-02
please post the output of **sudo apt-get update**.

You should see something like this:
```
dbott@dapper:~$ sudo apt-get update
Password:
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Get:4 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Get:5 http://security.ubuntu.com dapper-security/main Packages [76.7kB]
Get:6 http://security.ubuntu.com dapper-security/restricted Packages [6446B]
Get:7 http://security.ubuntu.com dapper-security/main Sources [14.0kB]
Get:8 http://security.ubuntu.com dapper-security/restricted Sources [960B]
Get:9 http://security.ubuntu.com dapper-security/universe Packages [38.8kB]
Get:10 http://security.ubuntu.com dapper-security/universe Sources [5094B]
Get:11 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:12 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:13 http://ca.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Hit http://ca.archive.ubuntu.com dapper-backports Release
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper/universe Sources
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-backports/main Packages
Hit http://ca.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ca.archive.ubuntu.com dapper-backports/main Sources
Hit http://ca.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 173kB in 2s (65.4kB/s)
Reading package lists... Done
```

If you see something like the messages below, try [this link]("http://www.ubuntuforums.org/showpost.php?p=1704004&postcount=41").

```
sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  The HTTP server sent an invalid reply header
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/restricted Packages
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/main Sources
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/restricted Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/multiverse Packages
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/multiverse Packages
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/multiverse Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/universe Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/universe Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg The HTTP server sent an invalid reply header [IP: 85.133.25 .23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg The HTTP server sent an invalid reply header [IP: 1 95.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg The HTTP server sent an invalid reply header [IP:  85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz The HTTP server sent an in valid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz The HTTP server sent an invalid reply head er [IP: 85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz The HTTP server sent an inva lid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz The HTTP server sent an invalid repl y header [IP: 195.248.90.54 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz The HTTP server sent an in valid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz The HTTP server sent an invalid re ply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz The HTTP server sent an invalid reply header [IP : 85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz The HTTP server sent an invalid reply head er [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz The HTTP server sent an invalid repl y header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz The HTTP server sent an invalid reply header  [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz The HTTP server sent an invalid reply head er [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz The HTTP server sent an invalid re ply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz The HTTP server sent an inva lid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz The HTTP server sent an invalid reply he ader [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz The HTTP server sent an invalid re ply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz The HTTP server sent an in valid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz The HTTP server sent an inva lid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz The HTTP server sent an in valid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz Connection failed [IP: 85.133.25.2 3 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Sef on 2006-11-02
> what happens when you try
sudo apt-get update
or
sudo aptitude update

It should update your repository list, so if you upgrade, then it will get you the newest packages in the repositories.

---

### Post by %hMa@?b&lt;C on 2006-11-04
> **Sef said:**
> It should update your repository list, so if you upgrade, then it will get you the newest packages in the repositories.

lol, i was tellimg him/her to try that and to post the output. I wasnt asking what it does;)

---

