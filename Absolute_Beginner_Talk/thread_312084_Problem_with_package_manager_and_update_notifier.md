---
title: "Problem with package manager and update notifier"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by arcarsination on 2006-12-03
Hey everyone,
I am very new to Ubuntu and have run into an error with the automatic updates and package manager.  For some reason every time I try to use the updater, it says that there's an error and it doesn't run.  I go to the package manager and the error reads:

E: Type '-e' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I really have no idea what that means...

---

### Post by kakalaky on 2006-12-03
Can you post the output of 'cat /etc/apt/sources.list'?

---

### Post by moshuptrail on 2006-12-03
archive servers are down

---

### Post by arcarsination on 2006-12-03
-e deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer
se multiverse
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un
iverse multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
(END) 

does that look right?

---

### Post by kakalaky on 2006-12-03
You need to remove the -e from the first line.

'sudo gedit /etc/apt/sources.list'

then remove "-e" from the first line and save the file.

---

### Post by arcarsination on 2006-12-03
wow
uhh that was easy
thanks alot kakalaky.

---

