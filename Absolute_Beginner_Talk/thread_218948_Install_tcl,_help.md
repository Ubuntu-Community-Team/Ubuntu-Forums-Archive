---
title: "Install tcl, help?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Denner on 2006-07-19
I want to install tcl, because i will have a eggdrop bot online, but its say i'm not have tcl on the system.

Is there a commando to install tcl? :)

---

### Post by MrHorus on 2006-07-19
```
apt-get install tcl
```

That should do it although it might be libtcl that you are looking for.

---

### Post by Denner on 2006-07-19
Doesn't work, its say some with the park tcl has no installion

(Its on danish, and I'm not good to english :|)

---

### Post by MrHorus on 2006-07-19
> **Denner said:**
> Doesn't work, its say some with the park tcl has no installion


Have you enabled the universe and the multiverse repositories in Synaptic Package Manager?

You will require these additional repositories to gain access to a lot of software packages.

---

### Post by Denner on 2006-07-19
How can i come there?

---

### Post by CnorthMSU on 2006-07-19
Perhaps you need to find a software repository which contains a Danish localized version of tcl. I don't know where to suggest you might find one, but there is some wiki help which addresses adding software repositories at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Scarpa on 2007-08-25
simply install tcl, if you're uncertain of the command just type "tcl" in your terminal. or if u want here is the cmd sudo apt-get install tclx8.3
:guitar:

---

### Post by Xzavier on 2007-09-19
heh try this:

sudo apt-get install tcl8.3-dev

i had the same issues and this corrected it

---

