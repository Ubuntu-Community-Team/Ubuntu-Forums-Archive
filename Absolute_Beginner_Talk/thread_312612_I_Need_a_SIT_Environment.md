---
title: "I Need a SIT Environment"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-04
So, I'm four days into my Linux experience and am loving every bit of it.

One of my first learning was that trying to install stuff from tar and deb files can get very hairy very quickly - I've reinstalled twice already.

So, I've decided to setup a Virtual Machine to use as a SIT environment. To that end I have successssfully installed the VMWare server and have added an Ubuntu virtual machine.

My question, at last, is
Is there a way to copy the current config of my system over to the VM version as is, or do I need to do a fresh install and rebuild of SIT everytime I want to sync my environments?

---

### Post by lamego on 2006-12-04
What is a SIT environment to start with ? Testing ?

---

### Post by dkenny on 2006-12-04
> **lamego said:**
> What is a SIT environment to start with ? Testing ?

Sorry: System Integration Testing

Basically I want the ability to create a VM replica of my current environment that I can test addition of packages before loading them to my 'real' environment.
(I hope that makes sense)


Thanks

---

### Post by dkenny on 2006-12-04
Would backing up the live environment and restoring to the VM work?

---

### Post by Thumper322 on 2006-12-04
> **dkenny said:**
> So, I'm four days into my Linux experience and am loving every bit of it.

One of my first learning was that trying to install stuff from tar and deb files can get very hairy very quickly - I've reinstalled twice already.

So, I've decided to setup a Virtual Machine to use as a SIT environment. To that end I have successssfully installed the VMWare server and have added an Ubuntu virtual machine.

My question, at last, is
Is there a way to copy the current config of my system over to the VM version as is, or do I need to do a fresh install and rebuild of SIT everytime I want to sync my environments?

Using .tars and .debs can prove messy, but if you use apt-get you should be fine.

If you want to copy your system config over, I'd suggest using **rsync**; make sure both the VM and the real computer can access each other, and use rsync with root permissions to copy over the relevant folders. (For example, /opt, /bin, /usr, etc...)

---

