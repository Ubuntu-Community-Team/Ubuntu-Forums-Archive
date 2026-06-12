---
title: "Apt-get update"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by parradux on 2006-11-22
I've just recently re-installed Ubuntu Edgy, and i'am having a problem already. Normally apt-get works. However this time I get this message: 

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


How can I fix this?

---

### Post by parradux on 2006-11-22
Ohh and this is apt get in general and I get this error as well: 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by gosh on 2006-11-22
Then you have several applications that try to install programs (synaptic, update-manager, apt-get, add/remove programs, ...).
You can only have one open at a time.

---

### Post by pandu.rs on 2006-11-22
quit synaptic (or any other package-managemtb application), then it shld work fine

---

### Post by costis on 2006-11-28
If you cannot pinpoint your exact application run 
```
 ps aux  | grep apt
```and then```
sudo kill -9 #PID#
```e.g.```
costis@sangre:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
costis@sangre:~$ ps aux  | grep apt
root      5485  0.0  0.1   1656   496 ?        SNs  13:38   0:00 /bin/sh /etc/cron.daily/apt
root      5497  0.0  0.4   3916  1872 ?        SN   13:38   0:00 apt-get -qq update
root      5540  0.0  0.3   3508  1380 ?        SN   13:38   0:00 /usr/lib/apt/methods/gzip
costis    5897  0.0  0.1   2800   568 pts/1    R+   14:04   0:00 grep apt
costis@sangre:~$sudo kill -9 5497
```

---

