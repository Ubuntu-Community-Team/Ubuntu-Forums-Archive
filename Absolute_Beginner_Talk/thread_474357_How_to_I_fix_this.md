---
title: "How to I fix this"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-06-15
I am trying to intsall cinelerra

jreynolds@jreynolds-desktop:~$ sudo apt-get install cinelerra 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libguicast (= 1:2.1.0-2svn2007424ubuntu3) but 1:2.1.0-2svn20070520 is to be installed
             Depends: libmpeg3hv (= 1:2.1.0-2svn2007424ubuntu3) but 1:2.1.0-2svn20070520 is to be installed
E: Broken packages

---

### Post by kevdog on 2007-06-15
What happens when you type

sudo aptitude .....

instead of 

sudo apt-get .....

---

