---
title: "install headers"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by slutbit on 2008-04-04
I have installed the 'openscenegraph' with 'synaptic package manager', and i have no idea what it was good for because it sure never installed any libs or headers. I tried to use an example program and type make but it couldnt find any headerfiles. So i tried copy paste to the /usr/header/ folder but nothing happened. Im having a course so i have to use openscenegraph with linux or unix, but ubuntu is waaay to advanced for me. i cant find any help myself cause i dont understand it even though i tried to learn it for 3 months.

---

### Post by LaRoza on 2008-04-04
There is a sticky in the Programming Talk on this, but the command for the standard headers is:

```

sudo aptitude install build-essential

```

---

### Post by Oldsoldier2003 on 2008-04-04
```
sudo apt-get install linux-headers-`uname -r`
``` will install the headers for your current kernel

---

### Post by slutbit on 2008-04-04
when i typed the build essential thing it loaded for a while and needed the ubuntu- disc. The linux-header command gave:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What exactly did these commands do?

The problem is still the same, it hasent installed any headers, the header dir is exactly as it was before. Is it better to 'chmod 777 include' the include dir and then paste the headers?? Or is there a better way?

---

### Post by Oldsoldier2003 on 2008-04-04
> **slutbit said:**
> when i typed the build essential thing it loaded for a while and needed the ubuntu- disc. The linux-header command gave:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What exactly did these commands do?

The problem is still the same, it hasent installed any headers, the header dir is exactly as it was before. Is it better to 'chmod 777 include' the include dir and then paste the headers?? Or is there a better way?

the command LaRoza gave you installs many pieces that are required to compile applications. the command I had you run installs the headers for whatever kernel you are running.

According to the output of the command you have the current headers installed already so the problem is elsewhere in your build.

---

### Post by slutbit on 2008-04-27
> **Oldsoldier2003 said:**
> the command LaRoza gave you installs many pieces that are required to compile applications. the command I had you run installs the headers for whatever kernel you are running.

According to the output of the command you have the current headers installed already so the problem is elsewhere in your build.

I forgot this thread. Nope, the problem were not elsewhere. I manually installed the headers by reshmoding the header dir, and i found libs to install on some site, dont remember where. Unfortunately they have forgotten to put it on the osg homepage. should send a letter to them and remind them bout their mistake.

---

