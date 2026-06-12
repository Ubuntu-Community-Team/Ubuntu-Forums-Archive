---
title: "Need help : error in VMware Server installation"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Valandil on 2006-10-21
Hello,

I've tried to install VMware Server on Ubuntu Dapper Drake. Unfortunately, after choosing where I wanted to install everything in VMware Server, this error message showed up 
[INDENT]
Unable to get the access rights of source file 

Execution aborted.[/INDENT]



It appears that there is no file named "bin" in the vmware-vix directory, as far as I'm concerned. Any tip on how to fix that?

Tell me more if you need more info.

---

### Post by blendmaster on 2006-10-21
You may have told it to install in a password protected directory.

choosing somewhere like /home/<your username> will be pretty safe

edit: This could also be a sudo problem, where you need to access the file through sudo

---

### Post by redDEADresolve on 2006-10-21
use this guide
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

and this one is you need to configure vm for your kernel
[http://ubuntuforums.org/archive/index.php/t-25258.html](http://ubuntuforums.org/archive/index.php/t-25258.html)

---

