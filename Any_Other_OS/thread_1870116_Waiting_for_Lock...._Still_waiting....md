---
title: "Waiting for Lock.... Still waiting..."
date: 2011-10-26
forum: Any Other OS
---

### Post by IMpeccable on 2011-10-26
Hello, I'm running a Mint4Win version of Katya Mint. I think it is based off the new version of Ubuntu, Oneiric? But, I am trying to install a package, and it is says it is waiting for lock... And it's still waiting...

EDIT: I am also trying to install Ubuntu Studio onto Mint.... Because Wubi would not work, and I do not feel comfortable repartitioning.

EDIT: I canceled those... and now nothing will install! AHHHHH!!!

---

### Post by Stigmata13 on 2011-10-26
If it mentioned a lock, that probably means that you have another application open using the administrative lock, which basically means you can only have one application installing a program at any one time, for example if you are installing something from the terminal you can't install something from the software center at the same time.

My advice would be to make sure you don't have any other program open that is installing something first. If you do, it is best to wait until it finishes and then try.

---

### Post by IMpeccable on 2011-10-26
Thanks, should I just try to reboot? Because I don't see any processes open

---

### Post by sffvba[e0rt on 2011-10-26
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by IMpeccable on 2011-10-26
Never mind, I realized that I was installing something, but Synaptic/Software Manager was not up

---

### Post by collisionystm on 2011-10-26
> **IMpeccable said:**
> Never mind, I realized that I was installing something, but Synaptic/Software Manager was not up

The dpkg lock will be placed any time an install is occurring whether it be by Terminal, Synaptic, or software center. One install at a time! Even Win. 7 is doing that now...

---

