---
title: "Installing nvidia-glx-new"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by tel93 on 2008-02-02
I have an Nvidia GV-NX62TC256D graphics gard (geforce 6200) and I want to install the nvidia-glx-new. I tried many things but I can't seem to get it to work. Help!

---

### Post by overdrank on 2008-02-02
> **tel93 said:**
> I have an Nvidia GV-NX62TC256D graphics gard (geforce 6200) and I want to install the nvidia-glx-new. I tried many things but I can't seem to get it to work. Help!

HI and could you give us a little more info. Did use use the restricted drivers? What problems are you having?

---

### Post by tel93 on 2008-02-02
> **overdrank said:**
> HI and could you give us a little more info. Did use use the restricted drivers? What problems are you having?

Currently I'm using the nvidia-glx-legacy drivers. I tried installing it via synaptic, via the command line, had a problem with envy and I just want the drivers to be installed.

---

### Post by overdrank on 2008-02-02
> **tel93 said:**
> Currently I'm using the nvidia-glx-legacy drivers. I tried installing it via synaptic, via the command line, had a problem with envy and I just want the drivers to be installed.

Ok what errors did you receive via synaptic and Envy? In your previous post it appears you had issues with updating and installing are these issues resolved?

---

### Post by tel93 on 2008-02-02
NO I can install some stuff in synaptic but most of it plus all debs i've downloaded are uninstallable.

Envy: dependency is not satisfiable dh-make
synaptic: Conflicts with nvidia-glx-legacyy (even after uninstallation!)

---

### Post by tel93 on 2008-02-02
Fixed software issue :)

---

### Post by overdrank on 2008-02-02
> **tel93 said:**
> NO I can install some stuff in synaptic but most of it plus all debs i've downloaded are uninstallable.

Envy: dependency is not satisfiable dh-make
synaptic: Conflicts with nvidia-glx-legacyy (even after uninstallation!)

HI and dh-make is a part of build essential for compiling.  You will have to enable multiverse and universe repositories, as described in point E of the [FAQ]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")
I have had a similar issue with the conflicts but maybe enabling the repos will help.
Edit I and glad it is working and I was to slow on the reply :)

---

### Post by tel93 on 2008-02-02
I enabled multiverse and universe repos, but I thought they were on by default! :)

---

