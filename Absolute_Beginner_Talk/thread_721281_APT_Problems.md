---
title: "APT Problems"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by bbharatsony on 2008-03-11
when I try to do

apt-get -f install
 
i get 

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


Can anyone help me with this horrible problem.

---

### Post by PmDematagoda on 2008-03-11
Are you running another package manager program or process? If so then close them and try running the command again.

---

### Post by jan quark on 2008-03-11
try

```
sudo apt-get -f install
```

and yes PmDematagoda's idea first

---

### Post by byenary on 2008-03-11
This always works :
rm /var/cache/apt/archives/lock
But its better practice to close to programs wich could have it in use

---

### Post by Seisen on 2008-03-11
> **bbharatsony said:**
> when I try to do

apt-get -f install
 
i get 

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


Can anyone help me with this horrible problem.

Its because you didn't add sudo in front of the command hence why it says "Permission Denied" Sudo will give you superuser privileges for a little bit of time.

---

