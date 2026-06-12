---
title: "Java not working in firefox"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-10-12
i have installed the restricted packages and the java plugin for firefox, but when i try to visit a site with java in grey boxes with the java symbol appear and a box appears asking me to accept the certificate. but whatever button i cliick(yes,no,always) firefox freezes then exits.
i am running feisty 64bit

---

### Post by hotweiss on 2007-10-12
I had problems with JAVA also, try to install it like this:

> 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

That worked for me.

---

### Post by simon303 on 2007-10-12
```
simon@simons-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
simon@simons-desktop:~$ 
```
i have tried to install on of those before and got the same error

---

### Post by slikwill on 2007-10-14
After the install of java6 a blue screen appears in the Terminal window with text that scrolls and ends with <Ok>.  is therre a response to this required, and how?  Do you just close the window to terminate?

---

### Post by avik on 2007-10-14
Actually, I'm not sure those packages are available for amd64.  Try looking here for any tips: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java").

---

