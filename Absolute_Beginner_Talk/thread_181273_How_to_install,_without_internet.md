---
title: "How to install, without internet?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by dontpanic0 on 2006-05-23
I have a laptop with ubuntu on, and I would like to install some programs on it.  However, I can't get my wireless adapter to work on it, and I have kindof given up trying.  So, I downloaded some programs on my desktop computer and copied them to my laptop using a flash drive.  They are usually some kind of archive, mostly rpms.  How do I install these programs?

---

### Post by Phlosten on 2006-05-23
Firstly you want .deb packages, and not RPM's. Ubuntu is built upon the Debian base, hence the .deb.

The best way I would suggest to solve your problem is browse [http://packages.ubuntu.com](http://packages.ubuntu.com) which lists all the packages available in the Ubuntu repositories. It also list dependencies for all the packages so you can also make a note of other files you will need. 
You can then download these manually from the Ubuntu repositories and they can be installed using 
"sudo dpkg -i packagename.deb"
Its a long process especially if you need lots of dependencies, but once you have installed a few you will find yourself needing less.

---

