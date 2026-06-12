---
title: "Installing Packages"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by echokilo on 2005-06-09
I just installed Ubuntu Server and have only the command prompt. Now I have some questions:

1) How do I find & install additional packages such as Samba and have them start at boot?

2) How do find & I retrieve other packages?

2) How do I configure the screen to use a higher resolution?

Remeber I only want to use the command prompt.

Thanks!

---

### Post by Kyral on 2005-06-09
Apt my friend, apt

apt-cache search <string> searches the Apt Repos

make sure your /etc/apt/sources.list has all the repos activated

and then, just sudo apt-get install <package>

I think if it is meant to start at startup, APT will take care of it

---

