---
title: "Upgrade to edgy using Kubuntu"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-27
What is the terminal command for the upgrade to edjy?  Also I am using kubuntu not ubuntu.  Thanks

---

### Post by John.Michael.Kane on 2006-10-27
[COLOR=Red]**You do this at your risk!!!**[/COLOR]```
sudo update-manager -c
```
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by firebirdworks on 2006-10-27
Didn't work
command not found

---

### Post by firebirdworks on 2006-10-27
matt@Home:~$ sudo update-manager -c
Password:
sudo: update-manager: command not found

---

### Post by John.Michael.Kane on 2006-10-27
```
kdesu kwrite /etc/apt/sources.list
```
replace all the words that have dapper to edgy

Then run these:
```
sudo aptitude update 
sudo aptitude dist-upgrade
```

---

### Post by firebirdworks on 2006-10-27
=```
 matt@Home:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
matt@Home:~$
 
```

---

### Post by Dual Cortex on 2006-10-27
Open konqueror and browse to /etc/apt/ then right click sources.list + select actions, then edit as root (something similar to that)

---

### Post by John.Michael.Kane on 2006-10-28
firebirdworks I amended my post. that should allow you to edit the files in kde.

---

### Post by firebirdworks on 2006-10-29
It won't let me save changes to sources.list.

---

### Post by Cynical on 2006-10-29
do you not have sudo? Try this,

```

su
update-manager -c 

```

---

