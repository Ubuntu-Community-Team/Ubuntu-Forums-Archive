---
title: "uninstalling application"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-09-13
I was trying to install vmware messed up, It gives me this error. I didn't install the right dependencies so when I loaded up instead of getting the setup screen i got nothing. After installing the right dependencies i can't run the install because it tells me i have vmware installed.

How do I unistall, so I can restall?

It gives me this error message

red@red-desktop:~/Downloads/vmware$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

red@red-desktop:~/Downloads/vmware$

---

### Post by smelly_sox on 2006-09-13
Hey red,

If U used a .deb or .ubuntu file to install vmware, in a terminal you could
*apt-get install vmware --reinstall*

Regards

---

### Post by Sef on 2006-09-13
Did you install using apt-get or aptitude?  Use the same one as you installed with.

---

