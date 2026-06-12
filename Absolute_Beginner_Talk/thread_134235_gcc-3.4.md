---
title: "gcc-3.4"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by thrakirr on 2006-02-21
sudo apt-get install gcc-3.4 doesn't work, here's the output. Any ideas?

sudo apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base
0 upgraded, 3 newly installed, 0 to remove and 113 not upgraded.
Need to get 2355kB of archives.
After unpacking 8720kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gcc-3.4-base 3.4.4-6ubuntu8 [163kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main cpp-3.4 3.4.4-6ubuntu8 [1707kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gcc-3.4 3.4.4-6ubuntu8 [484kB]
Fetched 719B in 0s (4892B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Exact same result when adding --fix-missing tag.
This is also being done directly after a successful apt-get update.
Help, please.

---

### Post by heimo on 2006-02-21
Something going on in the repositories. It's not your system. There are at least two other threads with same error messages, I bet it's already being taken care of and will be solved in couple hours. Try again later.

---

