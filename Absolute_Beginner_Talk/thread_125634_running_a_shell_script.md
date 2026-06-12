---
title: "running a shell script"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by georgey on 2006-02-04
Hi I am completely new to running a linux machine but have installed Breezy and all the installed programmes work just fine. However, I need a driver for my ATI graphics card and the ATI site suggests I run a small shell script called check.sh to work out which driver is required. However, I cannot figure out how to run this script. clicking on it in nautilus gives run options but these do nothing. Typing check.sh or sudo check.sh or even gksudo check.sh in a terminal window do nothing. I am in the correct directory and the attributes on the file are set to executable. I know this must be something very basic but help, please? 

Thanks

G

---

### Post by christhemonkey on 2006-02-04
If you type
```
sudo ./check.sh
```
This exzecutes a file in the present directory, as oppossed to one that is in your bin folder.

---

