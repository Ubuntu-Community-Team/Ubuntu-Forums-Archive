---
title: "reinstalling Ubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Cpt.Flint on 2007-02-27
So I used Automatix and I think I screwed my system hard... I guess I'll have to reinstall Ubuntu and this is what I want to ask - is there a way just to repair the system files? 
For example - if I put a Windows CD, a have an option just to repair my current instalation.
The point is that I installed plenty of software and I don't want to reinstall it again..

Any solution?

---

### Post by arochester on 2007-02-27
What does you computer do now?

---

### Post by Cpt.Flint on 2007-02-27
> **arochester said:**
> What does you computer do now?

I can't install the build-essential package, so I can't compile any software...
In the above topic I tried to fix the problem with no succes 
[http://ubuntuforums.org/showthread.php?t=371638]("http://ubuntuforums.org/showthread.php?t=371638")

---

### Post by arochester on 2007-02-27
It's spelt Galeon (one L) not Galleon (two Ls).

Galeon is available through my repositories. Build-essential is also available through my repositories. Have you got Synaptic Package Manager which is far better than Aptitude?

---

### Post by Cpt.Flint on 2007-02-27
> **arochester said:**
> It's spelt Galeon (one L) not Galleon (two Ls).

Galeon is available through my repositories. Build-essential is also available through my repositories. Have you got Synaptic Package Manager which is far better than Aptitude?

Yes I have the Synaptic package manager, but i can't install buuild-essential or g++ or whatever it needs from there either.

---

### Post by arochester on 2007-02-27
Open Synaptic and do a search for build-essential. Check and see whether it is installed. If necessary do a right-click on the (green?) square and choose  "Mark for reinstallation" then "Apply". Do the same for g++

---

### Post by lyceum on 2007-02-27
> **arochester said:**
> Open Synaptic and do a search for build-essential. Check and see whether it is installed. If necessary do a right-click on the (green?) square and choose  "Mark for reinstallation" then "Apply". Do the same for g++

It becomes green once instaled. Just mark the box next to the name of what you want. 

I have installed Automatix on many a machine with no problems, just wondering what made you think that was the problem? (If it is a problem, it will need to be fixed)

---

### Post by Cpt.Flint on 2007-02-27
When I do this, I get:

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be ins

---

### Post by gigaferz on 2007-02-27
why dont you add the installation cd rom(I mean ubuntu,kubuntu live) to the repositories?

I did it once,

---

