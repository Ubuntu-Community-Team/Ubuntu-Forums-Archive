---
title: "Help With Make Function"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by SuperPetRalf on 2007-01-25
I recently start using Ubuntu from a windows based system as i am a student and cant afford/wont pay £100 for a copy of windows so I thought it was time to move on.

Anyway long story short I am trying to intall a web srver using apache, When i try to use the "make" command I get  "make: command not found" returned.

I tryed using "man make" to loko at the manual see if I was doing somthink wrong and it returned no entry for make, so I assume the function is not installed.

How do I install it, much apreciate your help, SuperPetRalf.

---

### Post by taurus on 2007-01-25
```
sudo aptitude update
sudo aptitude install build-essential
```
That will give you make and a bunch of other related apps to build something from source.

---

### Post by SuperPetRalf on 2007-01-25
Thank you, your help greatly appreciated.

---

### Post by lamego on 2007-01-25
> Anyway long story short I am trying to intall a web srver using apache, When i try to use the "make" command I get "make: command not found" returned.
If you are not an experienced linux user you should look for the software on the official repositories.
To install apache2 you just need:
```
sudo apt-get install apache2
```

---

