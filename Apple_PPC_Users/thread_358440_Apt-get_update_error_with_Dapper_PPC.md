---
title: "Apt-get update error with Dapper PPC"
date: 2007-02-10
forum: Apple PPC Users
---

### Post by rrob100 on 2007-02-10
I am unable to complete apt-get update with my Dapper system for PPC I use an iBook G4 2005 version. Below is my error report -
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_powerpc.deb: subprocess new pre-removal script returned error exit status 102

The Samba package is being reported as broken has anyone else struck this?
I have tried sudo apt-get install -f to fix the broken package with no success. Any suggestions for getting around this problem would be appreciated.

---

### Post by fkdev on 2007-02-10
What happens if you run:
```
 sudo dpkg -r samba 
```

---

### Post by rrob100 on 2007-02-10
I tried sudo dpkg -r samba 
this is what I got in my terminal
(Reading database ... 121259 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba

---

### Post by rrob100 on 2007-02-10
Problem solved from this link [http://ubuntuforums.org/showthread.php?p=2121155]("http://ubuntuforums.org/showthread.php?p=2121155")
go to bottom of page for a quick solution.
The method that Florian Kulzer provided works for me:

[B]cd /etc/rc2.d/
ln -sf ../init.d/samba K09samba[/B]

See the following topic for more detail
[http://www.debianhelp.org/node/4073]("http://www.debianhelp.org/node/4073")

---

