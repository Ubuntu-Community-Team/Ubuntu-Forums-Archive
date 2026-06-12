---
title: "New error"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by traveler-1 on 2007-06-23
Error: Missing Dependency: /bin/sh is needed by package adobe-release

How do i fix this error. 
A link to read about it will do just fine. Only way to learn is to read and do.

Thanks.

---

### Post by Inxsible on 2007-06-23
Could you be more specific ?

What commands did you run, that you got this error?

---

### Post by traveler-1 on 2007-06-23
Here is the entire read out

root@mike-desktop:/home/mike# yum install /home/mike/Desktop/adobe-release-1.0-0.noarch.rpm
Warning, could not load sqlite, falling back to pickle
Setting up Install Process
Setting up repositories
No Repositories Available to Set Up
Reading repository metadata in from local files
Parsing package install arguments
Examining /home/mike/Desktop/adobe-release-1.0-0.noarch.rpm: adobe-release - 1.0-0.noarch
Marking /home/mike/Desktop/adobe-release-1.0-0.noarch.rpm to be installed
Resolving Dependencies
--> Populating transaction set with selected packages. Please wait.
---> Package adobe-release.noarch 0:1.0-0 set to be updated
--> Running transaction check
--> Processing Dependency: /bin/sh for package: adobe-release
--> Finished Dependency Resolution
Error: Missing Dependency: /bin/sh is needed by package adobe-release

Thanks for the reply

> **Inxsible said:**
> Could you be more specific ?

What commands did you run, that you got this error?

---

### Post by Inxsible on 2007-06-23
> **traveler-1 said:**
> Here is the entire read out

root@mike-desktop:/home/mike# yum install /home/mike/Desktop/adobe-release-1.0-0.noarch.rpm
Warning, could not load sqlite, falling back to pickle
Setting up Install Process
Setting up repositories
No Repositories Available to Set Up
Reading repository metadata in from local files
Parsing package install arguments
Examining /home/mike/Desktop/adobe-release-1.0-0.noarch.rpm: adobe-release - 1.0-0.noarch
Marking /home/mike/Desktop/adobe-release-1.0-0.noarch.rpm to be installed
Resolving Dependencies
--> Populating transaction set with selected packages. Please wait.
---> Package adobe-release.noarch 0:1.0-0 set to be updated
--> Running transaction check
--> Processing Dependency: /bin/sh for package: adobe-release
--> Finished Dependency Resolution
Error: Missing Dependency: /bin/sh is needed by package adobe-release

Thanks for the reply

If you are using any Debian based Linux distro, i dont think you can use yum to install a rpm package

---

### Post by traveler-1 on 2007-06-23
Error: Missing Dependency: /bin/sh is needed by package adobe-release

How do i fix this error. 
A link to read about it will do just fine. Only way to learn is to read and do.

Thanks.

---

### Post by Jimmyfj on 2007-06-23
You can get automatix2 and install the full adobe reader packet from there, if it's adobe reader you're referring to.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by traveler-1 on 2007-06-23
Thanks will try it.
:p

---

### Post by Crafty Kisses on 2007-06-23
> **traveler-1 said:**
> Thanks will try it.
:p

That should do the trick. :p

---

### Post by bapoumba on 2007-06-24
Merged threads.

---

