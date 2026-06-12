---
title: "Packages Being Held Back"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-08-06
So i'm getting a message that "packages have been held back" when updating ubuntu. This is what i get: 
"craig@craig-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev libcapi20-3 libcapi20-dev
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
craig@craig-desktop:~$"

How can I fix this so everything runs smoothly? I had installed Kernel 686 through synaptic but seeing as I did not need it as I don't have an intel core I removed it from synaptic and now get this. ANy help? Thank you! :)

---

### Post by Kingsley on 2007-08-06
Try sudo apt-get install -f.

---

### Post by Frak on 2007-08-06
I've heard of cases where some updates won't install for ripple effect reasons, which version of the Kernel did you install, was it automatic or invoked?

---

### Post by Tumpster on 2007-08-06
> **Frak said:**
> I've heard of cases where some updates won't install for ripple effect reasons, which version of the Kernel did you install, was it automatic or invoked?

I installed the 686 Kernel....


Also, 
craig@craig-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
craig@craig-desktop:~$

---

### Post by Nythain on 2007-08-06
sudo aptitude dist-upgrade
maybe aptitude will handle it better than apt-get

---

### Post by alienexplorers on 2007-08-06
Are you running synaptic at the same time?

---

### Post by Tumpster on 2007-08-06
I ran that suod aptitude and it took care of some things but i'm getting this message upon running update manager: 
"craig@craig-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev libcapi20-3
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
craig@craig-desktop:~$"

And no i'm not running synaptic at the same time.

---

### Post by Tumpster on 2007-08-07
Bump!

---

### Post by Fonsis on 2007-08-08
I have a similar issue with some other packages in 7.04 

apt-get upgrade -f
apt-get install -f
apt-get dist-upgrade -f

No joy. 
Any ideas?

---

### Post by capink on 2007-08-08
Maybe you have some packages set to hold in either dselect or aptitude databases. We can verify this using these commands:

```
sudo dpkg --get-selections | grep hold
```


```
sudo aptitude search ~ahold
```

---

### Post by Frak on 2007-08-08
Have you tried going to synaptic and choosing "Mark all Upgrades" then click "Apply" and see what happens. And if that doesn't work, going to the updates, and then forcing its update?

---

