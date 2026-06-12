---
title: "Alien"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by addisor on 2007-01-19
Trying to convert rpm to deb so as to install a canon printer, every time I try and run alien i get

rob@rob-desktop:~$ su alien bjfilter-common-2.50-2.i386.rpm
Unknown id: alien
rob@rob-desktop:~$ 

HELP???

---

### Post by bluefrog on 2007-01-19
sudo not su (su alien --> trying to switch to user alien...), and make sure alien is installed.

James

---

### Post by bodhi.zazen on 2007-01-19
How to alien:

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file)

---

### Post by je1117 on 2007-01-19
try this:

sudo alien -k bjfilter-common-2.50-2.i386.rpm

---

### Post by addisor on 2007-01-19
Sorted and thanks to both of you

---

