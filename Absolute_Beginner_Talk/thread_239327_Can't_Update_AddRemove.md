---
title: "Can't Update Add/Remove"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Jenova_Project on 2006-08-19
Hi.

I am able to use firefox to browse the internet, I can ping sites, but when I try to use Add/Remove programs and update, it fails and says 'The repository might be no longer available or could not be contacted because of network problems...'.

[http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

Does anyone have any ideas on how to fix this? Thanks.

---

### Post by slimdog360 on 2006-08-19
give it a few hours, they could be updating the servers.

---

### Post by Jenova_Project on 2006-08-19
Na, i've been trying this for a few days :(

---

### Post by slimdog360 on 2006-08-19
[http://psychocats.net/ubuntu/sources.php]("http://psychocats.net/ubuntu/sources.php")

try replacing your sources list and try it again. the link says what you should do.

---

### Post by Jenova_Project on 2006-08-19
I followed the instructions, and it still can't connect to the repositories. The output is as follows:


gksudo gedit /etc/apt/sources.list 
(gedit:5280): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.


sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting tErr [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

---

### Post by TripleE on 2006-08-19
Have you tried to go to [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) or any repo in your firefox browser to see if you can get to it.

---

