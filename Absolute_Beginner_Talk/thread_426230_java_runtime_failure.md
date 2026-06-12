---
title: "java runtime failure"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-04-28
I tried to install Java runtime. Because of my mistake I am getting this message. How to correct this.

ohm@ohm-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ohm@ohm-desktop:~$ 

thanks

---

### Post by crmanski on 2007-04-28
What happens when you run this?
> sudo dpkg --configure -a

---

### Post by taurus on 2007-04-28
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

