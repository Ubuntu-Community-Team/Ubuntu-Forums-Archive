---
title: "installing gcc on ubuntu 6.10"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by d_maniger06 on 2007-05-05
i have downloaded gcc from the net..it gave me a tar.bz2 archive..how then can i install this package in my ubuntu?..thanx..

---

### Post by DSn0wMan on 2007-05-05
I would just download the package from the repos. ```
sudo aptitude install gcc
```
You might also want to install the build-essential package that has many common compilers, and libraries needed for build from source.

---

### Post by aysiu on 2007-05-05
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
rm gcc*.tar.bz2
sudo apt-get update
sudo apt-get install gcc
``` The first command changes the directory to your desktop (where you've probably downloaded the .tar.bz2 file).
The second command deletes the .tar.bz2 file, because you don't need it.
The third command sees what software is available to install from the repositories.
The four command installs gcc from the repositories.

Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

