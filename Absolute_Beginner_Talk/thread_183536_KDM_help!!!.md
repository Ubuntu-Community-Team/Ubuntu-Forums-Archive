---
title: "KDM help!!!"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-05-28
i installed something which removed GDM and since then i m using KDM

but KDM do not allow root acess to me. please help

---

### Post by tkjacobsen on 2006-05-28
by default the root user is disabled in ubuntu. This wiki describes the matter:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by patrick295767 on 2006-05-28
[QUOTE=wolfmaniac]i installed something which removed GDM and since then i m using KDM

but KDM do not allow root acess to me. please help[/QUOTE]
  
Try not to start X with root !!
Not good 
  Use sudo command
or sudo bash 
if you need.
  
To install gdm :
apt-get -f -y install gdm
to remove it: 
apt-get remove gdm
  
To install kdm :
apt-get -f -y install kdm
to remove it: 
apt-get remove kdm
  
Greetz

---

