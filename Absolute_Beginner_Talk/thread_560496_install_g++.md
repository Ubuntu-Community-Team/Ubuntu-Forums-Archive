---
title: "install g++"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by digvijay on 2007-09-26
i am trying to install g++ but synaptic is not able to dectect one of the dependencies, so can someone tell me how to install manually by downloading from net

---

### Post by digvijay on 2007-09-26
when i try to install it says ...
g++-2.95:
 Depends: libstdc++2.10-dev but it is not going to be installed

or how can i the repository from which it is downloading package info..

---

### Post by wirelessmonkey on 2007-09-26
Just install build-essential, it includes all the gcc and build apps you need, w/ dependencies.

---

### Post by digvijay on 2007-09-26
apt-get install build-essential
is what i wrote but it says it does not find this package..

---

### Post by digvijay on 2007-09-26
apt-get install build-essential
is what i wrote but it says it does not find this package..

root@kimpossible:/home/digvijay/Desktop# apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@kimpossible:/home/digvijay/Desktop# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

---

### Post by wirelessmonkey on 2007-09-26
Try apt-get update && apt-get install build-essential

build-essential is included in the standard repositories,

---

### Post by LaRoza on 2007-09-26
> **wirelessmonkey said:**
> 
build-essential is included in the standard repositories,

I think it is on the install disk also.

---

### Post by digvijay on 2007-09-26
nope it did not work ...
it was not able to connect ... maybe because i am working under a proxy...
so how can we set proxy config..username, passwrd, port,host to apt-get

---

### Post by digvijay on 2007-09-26
soryy .. it is connected .. most of repository did not work but some are working,  
can u tell me how can add newer repositories to synaptic.....

---

### Post by Martin Witte on 2007-09-26
this page gives some references on how to manage repositories [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

