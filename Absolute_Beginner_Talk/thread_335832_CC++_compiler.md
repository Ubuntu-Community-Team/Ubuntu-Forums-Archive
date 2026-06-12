---
title: "C/C++ compiler"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-01-10
Hello,

I am new to linux, I dont know how to install C/c++ compilers in Ubuntu. Then I learned from the forums that It should be done with Synaptic by installin build-essentials but I have a problem with that. There isn't any build-essential package in Synatic. Tried it using 'sudo' but it says build-essential package doesn't exist. When I booted Ubuntu from live cd, build essential package is present in Synatic. So, something must have happened during installation. please help me out of this problem

Thanks.

---

### Post by meng on 2007-01-10
Try again
sudo aptitude install build-essential
to ensure it is installed

then try:
gcc -v
to see if gcc is present.

---

