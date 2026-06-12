---
title: "Installing php5"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Blaatann on 2006-07-20
Hi everyone

I'm having some small problems with trying to find the php5 binary on my machine. Apache is using php5, that much I'm certain of (through the phpinfo()-command), but I can't find an executable. I'm trying to install some weblog-backend that needs the path to the executable, but I'm just stumped. 

I've posted in the newbie forum since I'm not 100% sure of my ubuntu version..
```
cat /proc/version Linux version 2.6.17 (root@orthanc) (gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)) #1 PREEMPT Sat Jun 24 14:05:55 CEST 2006
```

I asumed the php5 binary would be named php5, just as php4 is, but i can't find it on my system. Am I missing a package, or is my install flawed? I've tried using both locate and various find-commands but I've so far gotten no results.

Any help would be much apreciated.

---

### Post by risbac on 2006-07-20
Did you try the "php" command? Just try ```
php /path/to/a/phpfile.php
```

It's working on my server, it's not a Dapper though, it's a Breezy customized. But the PHP installation is typical I think.

---

### Post by Blaatann on 2006-07-20
Well.. It turned out my installation was less than perfect.. So I yanked out everything even related to any version of php on the machine (apt-get remove php5* --purge) and installed php5, php5-common, libapache2-mod-php5 and all the different related packages over again. Somewhere in the carnage I got the binary filed installed as well. So now everything is peachy again. 

Thanks for the help anyway :)

---

