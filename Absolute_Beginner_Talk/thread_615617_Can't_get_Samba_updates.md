---
title: "Can't get Samba updates"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by asafm on 2007-11-17
Hi,

I have 3 updates which fails to download:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

Any idea on fetching it from an alternative location?

---

### Post by daviescr on 2007-11-17
Sorry I am not of much help but I think I had the same three update failures as you. In the past I have never had this problem. 

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden




I am using 7.10 on my desktop 

I use samba to connect to a ubuntu ~6.10 server for file sharing, web server, and the like.

The rest of the house in on OSX

 ~No problems to report other than the updates fail~ 

No windows and loving it

---

### Post by pondochris on 2007-11-17
I had the same thing last night. I just went to software sources and changed from "server for united states" to "main server" and I was able to download them @500kb/s.

---

### Post by chrome101 on 2007-11-17
Its working now... Ive been trying for last three days.

---

### Post by kleo skywalker on 2007-11-17
Exact same problem.
Though I have no idea what Samba is or what it does!

---

### Post by chamberlain2006 on 2007-11-17
This is a problem with the main servers repository.  You can fix it by going to System>Administration>Software Sources, and click Download from, and select other.  Then choose "Select Best Server".  It will run some tests, and find the fastest server.  Once it's done, click, Choose Server, and close.  This should find a good, fast server, so not only will the updates work, but they'll be faster, too!

---

### Post by jcats on 2007-11-17
Kleo; From 1 beginner to another, Samba allows you to connect,share files, etc. with Windows machines.

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

See if this answers your questions.So you may not need or want it.

jcats

---

### Post by kleo skywalker on 2007-11-17
> **chamberlain2006 said:**
> This is a problem with the main servers repository.  You can fix it by going to System>Administration>Software Sources, and click Download from, and select other.  Then choose "Select Best Server".  It will run some tests, and find the fastest server.  Once it's done, click, Choose Server, and close.  This should find a good, fast server, so not only will the updates work, but they'll be faster, too!

Worked, thanks.

---

### Post by asafm on 2007-11-17
> **pondochris said:**
> I had the same thing last night. I just went to software sources and changed from "server for united states" to "main server" and I was able to download them @500kb/s.

That helped!
Thanks!

---

