---
title: "amsn problem"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by djstarrock on 2006-10-23
i can't dowload amsn its saves as a deb i open it up its says 'error Dependency is not satisfiable: tcltls

---

### Post by public_void on 2006-10-23
Download it from the repos via Synaptic. All the dependencies will be taken care of.

---

### Post by djstarrock on 2006-10-23
but which one do i download

---

### Post by NoWhereMan on 2006-10-23
try this one..
[http://prdownloads.sourceforge.net/amsn/amsn-0.96RC1-linux-installer.bin](http://prdownloads.sourceforge.net/amsn/amsn-0.96RC1-linux-installer.bin)

---

### Post by djstarrock on 2006-10-23
which synaptic file do i download

---

### Post by NoWhereMan on 2006-10-23
"amsn"

btw, amsn in repository should be old :/

---

### Post by djstarrock on 2006-10-23
a what

---

### Post by Mornedhel on 2006-10-23
In the console :

sudo apt-get update
sudo apt-get install amsn

there you are.

You do not download a 'synaptic file'. You run synaptic, select which packages are to be installed, and Apply. That downloads (or gets from install CD) the required packages, taking care of possible dependencies, and installs everything where it needs to be installed.

Edit : The package name is amsn, just checked it.

---

