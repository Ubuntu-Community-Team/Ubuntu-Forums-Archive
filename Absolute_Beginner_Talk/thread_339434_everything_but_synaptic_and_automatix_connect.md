---
title: "everything but synaptic and automatix connect"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by limesky on 2007-01-15
Hello! Recently my ability to get new programs crashed? I did move my location, I am now back at college and I don't know if they've changed anything with their network, but I was able to connect with everything fine before I left and while I was at home. I get this message in Terminal when I run sudo apt-get update:

limesky@laptop-laptop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.35 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
10% [Waiting for headers] [Waiting for headers] [Waiting for headers]

Just for kicks I'm heading to an internet cafe tomorrow to see if it's just something new the school pulled on me, but I am hesitant about that being the problem because I am able to access whatever I need to on net, I'm using Kopete without any problems. 
I am running Dapper

Any thoughts?

---

### Post by Sef on 2007-01-15
Post your sources list here.

```
kdesu (terminal editor) /etc/apt/sources.list
```

I can't remember the name of the terminal editor for Kubuntu.  If you are using Ubuntu, it is gedit.

---

### Post by halw on 2007-01-15
> **Sef said:**
> 

I can't remember the name of the terminal editor for Kubuntu.  If you are using Ubuntu, it is gedit.

kate in Kubuntu

---

