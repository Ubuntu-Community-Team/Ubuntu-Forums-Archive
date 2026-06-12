---
title: "Ubuntu shell codes"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by trueface on 2008-01-11
Greetings my frien. i am new in this furom anbd new to ubuntu so please someone send me some shell codes for easy acces. tahnks

---

### Post by jflarm on 2008-01-11
I don't understand your question, what are you trying to do or learn?

---

### Post by az on 2008-01-11
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by bwtranch on 2008-01-11
Nice things to get to know:

/ is root, everything starts from there

cd is change directory

ls is list the contents of a dir

print is just that OK, example:, oh yeah, sudo su makes you root user and be careful with that one:

jim@jim-desktop:~$ sudo su
[sudo] password for jim:
root@jim-desktop:/home/jim# cd /
root@jim-desktop:/# ls
bin    dev   initrd      lib64       mnt   root  sys  var
boot   etc   initrd.img  lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  lib         media       proc  srv   usr
root@jim-desktop:/# cd home
root@jim-desktop:/home# ls
jim
root@jim-desktop:/home# cd jim
root@jim-desktop:/home/jim# ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
root@jim-desktop:/home/jim# cd Desktop
root@jim-desktop:/home/jim/Desktop# ls
root@jim-desktop:/home/jim/Desktop# bash
root@jim-desktop:/home/jim/Desktop# cd Pictures
bash: cd: Pictures: No such file or directory
root@jim-desktop:/home/jim/Desktop# cd / Pictures
root@jim-desktop:/# ls
bin    dev   initrd      lib64       mnt   root  sys  var
boot   etc   initrd.img  lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  lib         media       proc  srv   usr
root@jim-desktop:/# cd /frustration
bash: cd: /frustration: No such file or directory
root@jim-desktop:/# 

This is just an illistration your mileage may vary. Please se f___k  bash by an author that I can't remember and good luck :)

---

