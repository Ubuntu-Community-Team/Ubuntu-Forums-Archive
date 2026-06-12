---
title: "2 permission problems"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Violated on 2007-04-15
Hello,

i got 2 problems with permissions. if i try to a program using the apt-get install line, i get an error. here i tried to install unrar.

```
alex@BOVEN:~$ apt-get install unrar
E: can't open  '/var/lib/dpkg/lock'  - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

(roughly translated, running the dutch version of ubuntu)
so i tried manual installation, but that also failed. i couldn't copy the files to /bin, i didn't had the permission. i looked at properties > permissions, and only the root user could change that. Only, how to log into that user? 

Hope somebody can help :)

---

### Post by chamberlain2006 on 2007-04-15
To use administrative applications such as "apt-get", you have to use the prefix "sudo".  So, your command would become "sudo apt-get install unrar".  You will then need to put in your password to install.

---

### Post by Violated on 2007-04-15
Allright, got it working :) thanks mate.

---

### Post by taimel803 on 2007-04-16
i want to change apache2.conf, but i can't save it because i haven't got "permission"
so how to change permission

---

### Post by dstew on 2007-04-16
Same thing. Use **sudo gedit apache2.conf**, and when you have finished you can save it.

---

