---
title: "Trying to install"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by natman on 2005-11-29
I am trying to install a program called "polymake"
So i downlaod thepakage to my desktop and ran the following
> bunzip2 polymake-2.10.tar.bz2
tar -xvf polymake-2.10.tar
cd polymake-2.10
./configure
make
sudo checkinstall
and everything was fine until
> ./configure
and i got the responce> natman@bigb:~/polymake-2.1.0$ ./configure
****************************************************
Please be sure to read the installation instructions
before proceeding with the configuration procedure!
****************************************************
./configure: line 13: make: command not found


can anyone help? thanks

---

### Post by binks on 2005-11-29
have you installed the package build-essential from the repository

---

