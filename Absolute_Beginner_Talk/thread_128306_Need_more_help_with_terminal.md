---
title: "Need more help with terminal"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by Discretion on 2006-02-11
**Terminal Nightmare**
i am now trying to install webin apache front end....WHAT IS IT WITH THIS ROOT THING....
here is what i did and what hapend can anyone help..???
----------------------------------------------------------------------------------------------------------
mark@apache:~$ sudo -l
Password:
User mark may run the following commands on this host:
    (ALL) ALL
mark@apache:~$ cd webmin-1.260
mark@apache:~/webmin-1.260$ ./setup.sh /usr/local/webmin
***********************************************************************
*            Welcome to the Webmin setup script, version 1.260        *
***********************************************************************
Webmin is a web-based interface that allows Unix-like operating
systems and common Unix services to be easily administered.

**ERROR: The Webmin install script must be run as root**

mark@apache:~/webmin-1.260$

-----------------------------------------------------------------------------------------------------

---

### Post by Herman on 2006-02-11
```
sudo -i
```
Try sudo -i instead of sudo -l and see what happens. :D (Herman)

---

### Post by Discretion on 2006-02-11
thanks........sorry i have been at this hours and getting nowhere fast!!

now it say login incorect......ahhhhhhhhhhh!!!

its driving me MAD!!!!!!!

---

### Post by Lord Illidan on 2006-02-11
I see that you are using this command

```
 ./setup.sh /usr/local/webmin
```

What if you use this:

```
sudo ./setup.sh /usr/local/webmin
```

or this:

```
sudo sh setup.sh /usr/local/webmin
```

---

### Post by Discretion on 2006-02-11
you are a supper star!!!

---

