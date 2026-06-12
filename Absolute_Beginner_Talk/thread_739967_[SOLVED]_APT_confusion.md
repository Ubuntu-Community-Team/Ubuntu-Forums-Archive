---
title: "[SOLVED] APT confusion"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Line on 2008-03-30
Hi
I have downloaded a new program (EAGLE Layout Editor) as an RPM package, and i am little familiar with the APT program, I guess i just don't have enough power in my brain to have the APT program install this RPM package.. Can anyone help me out here? (I use ubuntu 7.10)

---

### Post by YoG%*@ on 2008-03-30
hi, 

you could use 'alien' to convert the rpm to a .deb package, and then install it the usual way. 

hth,
mux

[edit]
btw, i think eagle is available in the repos. you should be able to install it through synaptic!
[/edit]

---

### Post by aun on 2008-03-30
Apt won't install rpms directly, but you can use alien to convert the .rpm to a .deb.  I haven't done this a lot, but look around for instructions on alien.

---

### Post by mali2297 on 2008-03-30
> **mux said:**
> 
[edit]
btw, i think eagle is available in the repos. you should be able to install it through synaptic!
[/edit]

Yes, it's in the *multiverse* repository. In Synaptic, go to **Settings -> Repositories** and check that the repo is enabled. Then use the search function to find the package **eagle**.

---

