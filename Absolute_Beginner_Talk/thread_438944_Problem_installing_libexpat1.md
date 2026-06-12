---
title: "Problem installing libexpat1"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ByteofKnowledge on 2007-05-10
[FONT="Fixedsys"]apt-get install libexpat1
Reading package lists... Done
Building dependency tree
Reading state information... Done
libexpat1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up zimbra-spell (4.5.5_GA_838.UBUNTU6) ...
hostname: Unknown host
hostname: Unknown host
dpkg: error processing zimbra-spell (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zimbra-spell
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]

I have checked the etc/hosts and etc/hostname files and found them to be formatted how I have been instructed. What should I look for here?

---

### Post by ByteofKnowledge on 2007-05-10
Found it. I had a problem in my hosts file. Should look like this:
 
[FONT="Fixedsys"]127.0.0.1       localdomain.localhost localhost
10.x.x.x    mail.domain.com mail[/FONT]

---

