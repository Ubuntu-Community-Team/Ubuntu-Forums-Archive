---
title: "Mobile 915GM/GMS/910GML EXpress"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by torwul on 2006-08-06
Hi,

Im new to Ubuntu.I've installed it and it works and i love it. But there's a problem. I'have a ACER ASPIRE 9500 with a Mobile 915GM/GMS/910GML graphics card. 17inch screen 1400*900. But de resolution i've got is now 1024*786. Does someone have a solution for this. I don't think this is normal.

I also downloaded de latest driver but i don't know how to install it

greetings Torwul

---

### Post by Jagot on 2006-08-06
Thats Intel onboard graphics so you probably need 915resolution.  Enable the universe repository, then:

```
sudo aptitude update && sudo aptitude install 915resolution
```

It detected and configured my resolution correctly without me having to do any other configuration so see if it does the same for yours.  If not then it shouldn't be too difficult to configure.

---

### Post by torwul on 2006-08-06
hi,

i've done what you have written. This is the result

admin@ubuntu:~$ sudo aptitude update && sudo aptitude install 915resolution
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [44.2kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [11.0kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 91.5kB in 1s (50.8kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "915resolution"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
admin@ubuntu:~$

---

### Post by Jagot on 2006-08-06
You haven't enabled the universe repository.  See either of these links to accomplish this:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

