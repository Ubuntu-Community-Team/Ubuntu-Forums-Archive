---
title: "synaptic package manager won't work"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by mceven on 2007-06-05
Hello,

Another problem:  I'm trying to install programs using Synaptic package manager, and I can't open it.  I get this error message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
E: _cache->open() failed, please report.

My son installed Ubuntu on our computer today and deleted Windows and our files in the process -- in an attempt to get things working, I guess he clicked on an update icon in the upper right hand side of the taskbar (sorry, there's probably a different term for that) and then turned the computer's power off in the middle of the installation.  I'm guessing this is what's causing the problem.  Can anyone help me fix this?

---

### Post by sankarv on 2007-06-05
backup ur files if needed and go for reinstall (if u can again be patient enough to install any new packages which were installed after ubuntu install (if any)) since reinstallation takes not more than half an hour.

---

### Post by jonward0690 on 2007-06-05
Yea I have ran into this problems several times all I could do is reinstall the os but there is a good chance that someone on here that could help you.If they can I am interested in knowing this to.

---

### Post by jfinkels on 2007-06-05
> **mceven said:**
> Hello,

Another problem:  I'm trying to install programs using Synaptic package manager, and I can't open it.  I get this error message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
E: _cache->open() failed, please report.

My son installed Ubuntu on our computer today and deleted Windows and our files in the process -- in an attempt to get things working, I guess he clicked on an update icon in the upper right hand side of the taskbar (sorry, there's probably a different term for that) and then turned the computer's power off in the middle of the installation.  I'm guessing this is what's causing the problem.  Can anyone help me fix this?

Open the terminal (Applications > Accessories > Terminal) and type the following (or copy and paste):```
sudo dpkg --configure -a
```
Type your password and follow whatever directions it gives. If you need help come back.

If you manage to get that done okay, try  typing the following commands in the terminal (one at a time) afterwards:```
sudo apt-get -f install
sudo aptitude update
sudo aptitude upgrade

```
And your system will be all installed and up-to-date.

---

### Post by STREETURCHINE on 2007-06-05
to damned slow..

---

### Post by Ek0nomik on 2007-06-05
> **sankarv said:**
> backup ur files if needed and go for reinstall (if u can again be patient enough to install any new packages which were installed after ubuntu install (if any)) since reinstallation takes not more than half an hour.

Generally we don't tell users to "reinstall" as their first and only option if it is a widespread error.  ;)

Close Synaptic and anything using apt.

Try running:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```

Now try opening Synaptic.

---

### Post by mceven on 2007-06-05
That worked!  Thanks!

---

### Post by jfinkels on 2007-06-05
> **mceven said:**
> That worked!  Thanks!

See? The error messages you get aren't completely useless! :D

---

### Post by sankarv on 2007-06-05
thats a good howto indeed

---

