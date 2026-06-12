---
title: "[SOLVED] bluez updates"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2008-03-28
i have 3 updates related to bluetooth, bluez-utils, bluez-cups and libbluetooth2 showing up in my update manager, but they are greyed out. Does anyone know if and when they can be installed?

---

### Post by DBrocks on 2008-03-28
In a terminal:

```
 sudo apt-get install bluez-utils
```
```
 sudo apt-get install bluez-cups
```
```
 sudo apt-get install libbluetooth2
```

apt-get is your friend :)

~Dan

---

### Post by Seisen on 2008-03-28
Most likely they are missing a dependency which is why they are grayed out, I experienced that all the time when I was testing gutsy. I might take a few hours or even a few days but they will be able to be installed eventually.

---

### Post by DBrocks on 2008-03-28
> **Seisen said:**
> Most likely they are missing a dependency which is why they are grayed out, I experienced that all the time when I was testing gutsy. I might take a few hours or even a few days but they will be able to be installed eventually.

I tried it on my computer before i posted it, and it worked with apt-get. you give it a shot!

---

### Post by DBrocks on 2008-03-28
*Bump* Did that work?

---

### Post by Inxsible on 2008-03-28
> **DBrocks said:**
> *Bump* Did that work?
Sorry.....was at work !

here's what I got
```
sudo apt-get install bluez-utils
[sudo] password for inxsible
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bluez-utils: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
E: Broken packages

```

---

### Post by DBrocks on 2008-03-28
```
sudo apt-get install libc6
```
try that and see what happens.

---

### Post by Inxsible on 2008-03-28
> **DBrocks said:**
> ```
sudo apt-get install libc6
```try that and see what happens.I already have the latest libc6 installed. But I see that the new bluez-utils package requires libc6 to be 2.7-1 or greater whereas the Ubuntu repos have it at 2.6

So I will have to install libc6 2.7-1 ..In any case I am planning on switching to Hardy Heron...so its a non issue.

:-)

---

