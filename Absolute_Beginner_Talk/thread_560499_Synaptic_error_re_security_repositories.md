---
title: "Synaptic error re security repositories"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by phatdad on 2007-09-26
I am getting an error on Synaptic and also when running sudo apt-get update. Here's the error lines from my terminal after sudo apt-get update
........
Failed to fetch 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [106kB]
99% [4 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
..........
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages          
  Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
...........

edit
and now it's not happening for some reason

---

### Post by dellinger on 2007-09-26
I'm guessing there was a problem server-side. I hit an error doing an update earlier today as  well (not sure what the exact error was), but rerunning the adept updater solved the problem for me. I just reran sudo apt-get update again to be sure and did not run into any problems.

---

