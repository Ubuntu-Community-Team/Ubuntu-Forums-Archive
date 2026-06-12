---
title: "Software Updates?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by nipjacks on 2006-11-09
When I go to update the software in the package manager it gives me an error about the repositories. what does this mean? I just want to update the software.

---

### Post by ThrobbingBrain66 on 2006-11-09
what specifically does the error say?

---

### Post by Kateikyoushi on 2006-11-09
Usually this happens when your sources list contains errors.

```
cat /etc/apt/sources.list
```

---

### Post by nipjacks on 2006-11-09
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by ThrobbingBrain66 on 2006-11-09
it should also have given a clue as to which repo it is.  it may just be an error in a repo or the repo may actually be gone.  could you please post which repo is or just post your whole sources.list?

```
gedit /etc/apt/sources.list
```

---

### Post by nipjacks on 2006-11-10
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.35 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.35 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.35 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]

---

### Post by Super King on 2006-11-10
Are you able to access the internet like normal?

---

### Post by ronmarley1 on 2006-11-10
nipjacks, are you connected to the Internet?

---

### Post by nipjacks on 2006-11-10
yes im connected. Unless im talking on the web forum by ESP.

---

### Post by nipjacks on 2006-11-10
what do i have to do if it wont connect to the repositories?

---

### Post by ronmarley1 on 2006-11-12
> **nipjacks said:**
> yes im connected. Unless im talking on the web forum by ESP.
Sorry for the suggestion.  My ESP let me down when I assumed that the computer you were using was not connected to the web.  Your symptoms indicated that you might not be connected, and there is the possibility that you were using another computer to write your post.  Good luck solving your problem.

---

