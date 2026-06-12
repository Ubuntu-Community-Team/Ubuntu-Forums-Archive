---
title: "Installing a Package"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by dryder on 2007-02-18
Hi,

I've updated all the packages to show in the various groups of what is available.

BOINC was amongst them - I didn't want boinc mngr or boinc seti as I want to attach to project manager. So I ticked the packages to install, one of which required extra library files off the Ubuntu CD.

It said they were installed - but BOINC isn't there to run as a program.

By saying they were installed, is Ubuntu saying it is ready for me to install them into the system as a program using sudo get/install ... ??

I guess the logical next q is does sudo get only 'get' from packages listed?

Many thanks,

David :)
P.S - searching previous posts did not help with this understanding ..

---

### Post by an.echte.trilingue on 2007-02-18
While connected to the internet:

```
sudo aptitude update
sudo aptitude install boinc*
```

Take care
-mat

---

### Post by Maestro23 on 2007-02-18
> **dryder said:**
> Hi,

I've updated all the packages to show in the various groups of what is available.

BOINC was amongst them - I didn't want boinc mngr or boinc seti as I want to attach to project manager. So I ticked the packages to install, one of which required extra library files off the Ubuntu CD.

It said they were installed - but BOINC isn't there to run as a program.

By saying they were installed, is Ubuntu saying it is ready for me to install them into the system as a program using sudo get/install ... ??

I guess the logical next q is does sudo get only 'get' from packages listed?

Many thanks,

David :)
P.S - searching previous posts did not help with this understanding ..

Some links you should read/bookmark: 

Installing in Ubuntu:
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To find the BOINC .bin(executable), open a terminal and type:

which BOINC (should give you the path to the .bin file).  Once you have the path, you can create a desktop launcher or add it to a menu.

Also can use:

whereis and locate commands.

Good luck.

---

### Post by dryder on 2007-02-18
> To find the BOINC .bin(executable), open a terminal and type:

which BOINC (should give you the path to the .bin file). Once you have the path, you can create a desktop launcher or add it to a menu.

May I ask if something is missing here?


The Synaptic Packages I installed were: boinc-client 5.4.11-1 and boinc-dev 5.4.11-1.

david

---

### Post by Maestro23 on 2007-02-18
> **dryder said:**
> May I ask if something is missing here?


The Synaptic Packages I installed were: boinc-client 5.4.11-1 and boinc-dev 5.4.11-1.

david

What is the output of the :

which BOINC

---

### Post by dryder on 2007-02-18
Hi

> What is the output of the :

which BOINC

I think I must be misunderstanding something - sorry.

I opened Terminal - typing sudo which BOINC or just which BOINC gives no result.

Please bear with me while I get used to Terminal ...
David

---

### Post by Maestro23 on 2007-02-18
> **dryder said:**
> Hi



I think I must be misunderstanding something - sorry.

I opened Terminal - typing sudo which BOINC or just which BOINC gives no result.

Please bear with me while I get used to Terminal ...
David

Hmmm.. I have never used BOINC, sorry.  That command will usually lead you to a program's .bin file.  Maybe someone who has used BOINC will chime in on this post.

---

