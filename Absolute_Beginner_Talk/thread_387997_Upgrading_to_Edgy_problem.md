---
title: "Upgrading to Edgy problem"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by DarkOdysseus on 2007-03-18
I am currently using Dapper Drake and need to upgrade to Edgy Eft. My update manager says I dont need any updates and there isent a choice to upgrade to Edgy Eft. Can someone show me how to upgrade to Edgy. maybe from the terminal.

---

### Post by zvacet on 2007-03-19
[https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28edgy%29%7C%28upgrades%29]("https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28edgy%29%7C%28upgrades%29")

---

### Post by Toadmund on 2007-03-19
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
##deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

```
If you put that in your etc/apt/sources.list it will update, not sure if that is the ideal way, a member here pasted it on a thread. 

Here, the member is Afonic: [ur]http://www.ubuntuforums.org/showthread.php?t=382547&page=3[/url]

---

### Post by Toadmund on 2007-03-19
OK, couldn't edit that; here:
[http://www.ubuntuforums.org/showthread.php?t=382547&page=3]("http://www.ubuntuforums.org/showthread.php?t=382547&page=3")

---

### Post by jmoro on 2007-03-19
i used this command and it gave me the update opition

 gksu "update-manager -c"

---

