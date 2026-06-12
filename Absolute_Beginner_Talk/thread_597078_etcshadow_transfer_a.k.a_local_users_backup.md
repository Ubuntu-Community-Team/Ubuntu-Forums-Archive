---
title: "/etc/shadow transfer a.k.a local users backup"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Clickbg on 2007-10-30
Hello community, I use Slackware since 2005 but the project basically dieing, so i decide to change my server os, but i have more than 100 local users. I search all over google for solution but... So my question is, does someone know how if it is possible i can transfer my local users from Slackware to Ubuntu Server without changing passwords? Thanks.

---

### Post by djdicbob on 2007-10-30
You cannot transfer the passwd file straight up....but you can turn shadow passwords "off" 

On slackbox:  Turn off shadow passwords
                       Copy passwd file to UbuntuBox

On ubuntubox: Turn off shadow passwords (example below)
                          Copy passwd file from slackbox to /etc on ubuntubox
                          Turn shadow passwords on

Ubuntu Server:

```
sudo shadowconfig off
``` 
&
```
sudo shadowconfig on
```


Should be that simple, but you will loose any password aging information contained in the passwd file.

---

