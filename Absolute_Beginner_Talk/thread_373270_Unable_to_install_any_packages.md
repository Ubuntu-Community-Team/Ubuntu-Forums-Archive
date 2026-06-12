---
title: "Unable to install any packages"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by claws_crystal on 2007-03-01
I downloaded g++( c++ compiler) from net, It appears something like .tar.bz2 file. I tried to install using GDebi package installer for installing but it is displaying msz "Could not open file,
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file"
I'm able to open through archive manager but i don't know how to install from those files
Plz help me installing compiler

---

### Post by Anicka on 2007-03-01
First, why don't you use synaptic or aptitude to get g++? It is available there.

Second, to handle packages (tar, gz, whatever) I think you need build-essential which also can be found in synaptic and aptitude. (Build-essential actually depends on g++ so you cannot get that g++-package from "outside" without having it installed from the repos first)

---

### Post by claws_crystal on 2007-03-01
Problem is that I am unable to install any of packages that are not available on synaptic

---

### Post by energiya on 2007-03-01
That is (I think) the source, and it must be compiled. But wasn't g++ in the repository? Did you added the extra repositorys?

---

### Post by anaconda on 2007-03-01
I think the build essential package is even included to the ubuntu liveCD.. it just isn't installed by default.

So if your reason to download it from somewhere elese than ubuntu repositories is that your computer isn't connected to the net you could install it from your install cd..

---

### Post by claws_crystal on 2007-03-01
Problem is not only with g++.... every package

---

### Post by Anicka on 2007-03-01
> **claws_crystal said:**
> Problem is that I am unable to install any of packages that are not available on synaptic

This is from the fact that build-essential is essential to build (or in your case "un-build") packages and archives.

---

