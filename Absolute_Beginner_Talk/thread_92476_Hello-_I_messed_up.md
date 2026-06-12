---
title: "Hello- I messed up"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by osgoor on 2005-11-19
Hello to all from a nubie...

In trying to get my new install of ubuntu to communicate with my wireless network, I deleted my host name. Now when I try to log in I get the warning message: Could not look up internet adress for ???. 
The ??? is what I entered and deleted. It says I may be able to add it back in under /etc/hosts but in trying that, I see that the file is read only and I can't edit it.

Please help the new guy !!

---

### Post by souki on 2005-11-19
do you mean you can log into console mode?
if you do, try to put 'sudo' before your command, eg:
```
sudo nano /etc/hosts
```
then, you will be asked for the administrative password

---

