---
title: "Running VMware within a virtual session?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-12-21
I know the first thing your thinking about is... why the beep would you want to do that right?

Well, I'm running Windows XP and have created a Ubuntu 7.10 virtual session in VMware workstation.

From this virtual Ubuntu 7.10 session, i'm trying to install VMware workstation for linux (using rpm file --> converted to deb using alien).

However, this isn't working.... is this even possible or am I barking up the wrong tree here? The reason i'm doing all this is because I want to test installing VMware on this PC's "virtual ubuntu" before I install it for real on my Ubuntu 7.10 run laptop.

Ideas? :confused:

---

### Post by wormser on 2007-12-21
Converting an .rpm is not needed.  There is a version of VMware Server in the repositories.  System> Administration> Synaptic Package Manager> Search for VMware.  I got a crazy idea.  Let's see how many VMs we can run in a VM. lol

Virtualbox is more popular with most Ubuntu users.  You might want to look at it also.

---

### Post by tonycm1 on 2007-12-21
Does VMware server or virtualbox also allow for creation of virtual image with windows install CD?

I was under the impression that only VMware Workstation could do this?

---

### Post by wormser on 2007-12-21
> **tonycm1 said:**
> Does VMware server or virtualbox also allow for creation of virtual image with windows install CD?

I was under the impression that only VMware Workstation could do this?

Yes, VMware Server and Virtualbox allow you to create VMs with CDs or .iso images.

---

