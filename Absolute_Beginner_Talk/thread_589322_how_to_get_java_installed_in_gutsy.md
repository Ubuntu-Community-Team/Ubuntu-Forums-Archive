---
title: "how to get java installed in gutsy?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-10-24
how to get java installed in gutsy?

---

### Post by techno-mole on 2007-10-24
have you tried the repo's ?
or you could try clicking on applications - add/remove programs -  and then searching for java.
thats how i did it, although for some reason it wouldnt install java webstart 6, something to do with it not being supported or something.
cheers

---

### Post by WedgeHG on 2007-10-24
This is what to do in Edgy. I think it ought to be the same in Gusty but I'm not positive. Can someone else confirm?

If you are looking for the firefox plugin open up a terminal (Applications- Accessories- Terminal).
Then type 

```
sudo apt-get install j2re1.4-mozilla-plugin
```

---

### Post by tashmooclam on 2007-10-24
I got it using the synaptic package manager.
System>Administration>synaptic package manager.
I clicked the button "search" in the package manager window.
In the search field: java 6
Scroll down. 
The sun-java6-jre is what I selected.
Click the box to the left of sun-java6-jre >"mark for installation".

---

### Post by Caffeine_Junky on 2007-10-24
yep, a search for "java" in: Applications >Add/Remove, ... will produce results for you, ...have a look at the "Ubuntu Restricted Extras" package as well.   

Show: All available applications.    Search = extra

...read the description of the package, it contains some good stuff you may be interested in, ..it contains java etc...

---

### Post by escobar_ on 2007-10-24
I installed mine using

```
sudo aptitude install sun-java6-jre
```

---

### Post by erginemr on 2007-10-24
But to do this (installing java from synaptic or with aptitude), you may need to enable other repositories (such as restricted, multiverse and universe) from the Synaptic Menu -> Repositories, first.

---

