---
title: "Segmentation fault when trying to install software"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by happysmileman on 2008-02-09
I'm on Kubuntu 7.10 and Adept Installer, adept manager and apt-get all Seg Fault when ever I try use them.

All Seg fault when building dependency lists, which I'm assuming means that the database is corrupted or the last download got corrupted, so deleting and redownloading it would probably fix it, but I don't know which file exactly is being used. :(

---

### Post by taurus on 2008-02-09
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by happysmileman on 2008-02-09
> **taurus said:**
> What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
"sudo apt-get update" works fine.
But then it seg faults when I run "sudo apt-get upgrade".

> 
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

Attached, but I haven't added or removed any repositories since I installed Kubuntu, and I don't think I've activated/de-activated any either.

Oh, and this happened just after I installed the "moodbar" package on Kubuntu. Now it crashes while checking dependencies, so installing that may have messed it up, but of course, if I try uninstall it, I get a seg fault.

---

### Post by happysmileman on 2008-02-09
Bump :(

---

### Post by asmoore82 on 2008-02-09
try this from a terminal:```
sudo dpkg --audit
```

---

### Post by happysmileman on 2008-02-09
> **asmoore82 said:**
> try this from a terminal:```
sudo dpkg --audit
```

Still gets seg faults when trying to run apt-get (or adept manager/installer).

---

### Post by asmoore82 on 2008-02-09
```
sudo apt-get check
```

if that still doesn't help, you should be able to remove the offending package like this:
```
sudo dpkg --purge moodbar
```

---

### Post by happysmileman on 2008-02-09
> **asmoore82 said:**
> ```
sudo apt-get check
```

That seg-faults as well.
```
paul@paul-desktop:~$ sudo apt-get check
[sudo] password for paul:
Reading package lists... Done
Segmentation fault (core dumped)
```

---

### Post by asmoore82 on 2008-02-09
*Bump - edited above post^^

---

### Post by happysmileman on 2008-02-09
> **asmoore82 said:**
> if that still doesn't help, you should be able to remove the offending package like this:
```
sudo dpkg --purge moodbar
```

Thanks, this worked, finally. :p

---

