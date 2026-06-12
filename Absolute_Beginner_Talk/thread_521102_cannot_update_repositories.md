---
title: "cannot update repositories"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by football0552 on 2007-08-09
Sooo everytime i try to install a program or reload/update the repositories they return these error codes, and I cannot figure out how to fix it. Any help?
I can get ubuntu updates automatically but it won't let me install anything from the repositories like i said.


Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [Working]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  Sub-process gzip returned an error code (1)
99% [7 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
99% [8 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 8B in 2s (4B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by sad_iq on 2007-08-09
Try removing the us from all the repositorys you use, so this line :
```
deb [http://**us.**archive.ubuntu.com](http://**us.**archive.ubuntu.com) feisty/main 
```
will become
```
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main 
```
Also make sure synaptic isn't running while you type sudo aptitude update in the terminal (a reboot could fix some of your other errors!).

---

