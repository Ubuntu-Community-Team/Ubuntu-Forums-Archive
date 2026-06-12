---
title: "E: Error:"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by GGates on 2007-06-06
I keeping getting this error message whenever I try to update or use synaptic package manager

Here goes the output error message:

E: ERROR: could not create configuration directory /root to/home/izzy/.synaptic -mkdir(2 No such file or directory)


I do not know what to do any help will be appreciated.

Thanks in Advance.

---

### Post by FleetAdmiral74 on 2007-06-06
Hmm. Well, maybe try just making the directory lol. idk, im new...

so brows the the home folder, and type somethine like 
mkdir .synaptic

i hope this works...

---

### Post by GGates on 2007-06-06
I ran locate .synaptic | less

the results where:

/root/.synaptic

now I do not understand this path:

/root to/home/izzy/.synaptic

What's root to??


Plz help as I can not install, update nor run synaptic package manager

---

### Post by gaspo on 2007-12-09
hi there, i have the solution, it works 100%

Create the root directory first before creating .synaptic like below:
open the terminal and tape

sudo mkdir /root
sudo mkdir /root/.synaptic

then run synaptic or root terminal, and it will work :popcorn:
cheers

---

