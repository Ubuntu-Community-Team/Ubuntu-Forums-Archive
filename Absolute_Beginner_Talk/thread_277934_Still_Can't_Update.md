---
title: "Still Can't Update"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by celim on 2006-10-15
```
celim@celim-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://au.archive.ubuntu.com dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://au.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out

```

Hope someone can help me with this :confused:

---

### Post by AndyCooll on 2006-10-15
Please post your sources list.

Easiest way to do this is to type in a terminal (Applications-->Accessories-->Terminal):
```
gedit /etc/apt/sources.list
```

:cool:

---

### Post by Kateikyoushi on 2006-10-15
He has a problem with resolving adresses might be a sideeffect of IPV6. Firefox works now.

I recommended to get the DNS address from his other machines and add it to his resolv.conf 
I assume it would be overwritten upon every boot, so does anyone have a better idea ?

---

### Post by celim on 2006-10-15
```
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```


But my DNS address is the same as
> celim@celim-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
Can u pls explain y i do need to add it?
I have tried to disable ipv6 as you said it might b the side effect
bye bye to ipv6

---

### Post by Kateikyoushi on 2006-10-15
The problem isn't in your list, I can open any of those addresses even you can with firefox, but apt can't.

I saw an example when adding the DNS address to the resolv.conf solved the same problem, but maybe someone can come up with a better, permanent solution.

---

### Post by celim on 2006-10-15
you are right. plug it into FF thn it can reach
but any update cannot b done via apt nor update manager nor synaptic
tis resolve.conf is tricky
delete it - it will appear again
overwrite - no effect
but i alr disable ipv6 through procedures post in the forum

---

