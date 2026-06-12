---
title: "Opera won't install, error - dependencies??"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-16
I add the opera web site to the sourse.list (according to the ubuntu opera wiki page) and did "sudo apt-get update" and then "sudo apt-get install opera" but it didn't install.  This was the result:

brian@ubuntu:~$ sudo apt-get install opera

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  opera: Depends: xlib6g (>= 3.3.6) but it is not installable or
                  xlibs but it is not installable
         Depends: libqt3c102-mt but it is not installable
E: Broken packages

---

### Post by yager on 2006-06-16
You may want to look into Automatix.  It will install Opera for you with no issues.  You do not have to install everything.  Just pick and choose the apps that you want to use.

---

### Post by WADemosthenes on 2006-06-16
Worked like a charm, and helps me with many other things as well!

---

