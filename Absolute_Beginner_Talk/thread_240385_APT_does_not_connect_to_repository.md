---
title: "APT does not connect to repository"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Paul Yard on 2006-08-20
Probably the right subject would be "silly question" but there are too many.
I just installed ubuntu and I am trying to update my package list.
/etc/apt/source.list was all commented because the connection was not working at the moment of the installation.
I uncommented the necessary lines and ran aptitude update but I always get error   
"..... Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
...."

I need some help.

Thanks 
py

I had a look to similar threads and I see the question is actually not so silly.
I have no proxy but I use a router with dhcp. 
I deleted all lines related to proxy from apt.conf.
Still aptitude update does not work.

help please!

---

### Post by mlind on 2006-08-20
You can try switching to another mirror. What's the country you're living in or the closest country on this list [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) ?


You need to edit /etc/apt/sources.list file and replace current repository location with a mirror

Here's a example that uses one of the mirrors listed in USA
```

deb http://mirror.cs.umn.edu/ubuntu **dapper** main restricted universe multiverse
deb http://mirror.cs.umn.edu/ubuntu **dapper-updates** main restricted universe multiverse
deb http://mirror.cs.umn.edu/ubuntu **dapper-security** main restricted universe multiverse

```

You need root privileges to edit this file, use editor of your preference. Like nano or gedit.
```

sudo gedit /etc/apt/sources.list

```

---

### Post by nanotube on 2006-08-20
> **Paul Yard said:**
> Probably the right subject would be "silly question" but there are too many.
I just installed ubuntu and I am trying to update my package list.
/etc/apt/source.list was all commented because the connection was not working at the moment of the installation.
I uncommented the necessary lines and ran aptitude update but I always get error   
"..... Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
...."

I need some help.

Thanks 
py

I had a look to similar threads and I see the question is actually not so silly.
I have no proxy but I use a router with dhcp. 
I deleted all lines related to proxy from apt.conf.
Still aptitude update does not work.

help please!

i see you've seen some of the old posts about this... have you made sure that internet works for other things (like browsing the web)?

---

### Post by Paul Yard on 2006-08-21
I have tried different mirror lists and I ran sudo aptitude update.
Furthermore Internet works perfectly from this computer.

Can you post me a sample of your apt.conf?

Thx
py

---

### Post by mlind on 2006-08-21
> **Paul Yard said:**
> I have tried different mirror lists and I ran sudo aptitude update.
Furthermore Internet works perfectly from this computer.

Can you post me a sample of your apt.conf?

Thx
py

My apt.conf looks like
```

APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";

```

> 
Could not connect to au.archive.ubuntu.com:80 (**1.0.0.0**)


Are you using a proxy? In that case you should probably modify apt to use that proxy
```

Acquire::http::Proxy "*http://proxy.server.com*:8080"

```

---

### Post by Paul Yard on 2006-08-21
I'm not using a proxy but I have a router with dhcp.
Maybe that's the problem.

My apt.conf now is completely blank but previously it was like yours.
So again, that's not the solution.

py

---

