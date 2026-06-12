---
title: "Cant login as ROOT..please help.."
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-14
Hi guys..

During the installation I was asked to create a user account.. anyway all this time i was working as a normal user and then i wanted to switch to root.
so I restarted and then in the login screen i said "root" for login name and then put my password, then it said "Administrators are not aloowed to use this login screen"..!
Now I dont know how to login as the root..
Anybody know how to do it..?
Thanks alot guys..!

---

### Post by aysiu on 2006-01-14
You don't need to log in as root to make root changes. See the third link of my signature for more details.

---

### Post by patrick295767 on 2006-01-14
U can always use sudo, eg.
  
```
sudo apt-get -f install rox-filer
```
for instance
  
--
or, If u'd like to use the root: 

```
sudo su
```
enter passwd u mentioned during installation
  
then:
```
passwd
```
  
And redefine ur root password then.
  
Ur root account will be active
=====
It's recommeanded to use sudo 
  
Greetz
  
Pat'

---

### Post by madu on 2006-01-14
Thanks a lot guys..!!
Yes.. using sudo is like admin..
Anyway i just logged in as root just to check..
Thanks a lot guys...!!

---

