---
title: "Trouble adding software"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by leon7250 on 2007-02-12
I have edited the Source.list file and when trying sudo aptitude update i keep getting this error !!

sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                                                
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_US                                     
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                              
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Translation-en_US                               
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
25% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

It just hangs at 25% until it times out.

Any help would be great!!

---

### Post by jpeddicord on 2007-02-12
Part of the error is because something else is using APT. Make sure nothing else is running that manages packages (Add/Remove, Update Manager, apt-get, Synaptic, etc.). If it still complains, restart in recovery mode from the GRUB menu and type `apt-get dist-upgrade`.

Jacob

---

