---
title: "Having problem with glibc-2.5"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by doris on 2008-04-16
Hi,

Anyone can help me?
I try to install libc6-dev in my machine. 
I having problem during build glibc-2.5!! 
It said no rule to make target '/home/ipr/Desktop/temp/glibc-2.5/glibc-build/Versions.all' needed by '/home/iprDesktop/temp/glibc-2.5/glibc-build/abi-versions.h'.

What should i do now? :(

---

### Post by Air_Scythe on 2008-04-16
I think u have to use ./configure first

---

### Post by doris on 2008-04-16
I got execute the configure file inside the glibc-2.5.
When i try to build with "make", i will get that  error. 
Am i missing something? :-|

---

### Post by Air_Scythe on 2008-04-17
First go into system/administration/synaptic package manager

then go into settings/repositories

click on updates and under ubuntu updates tick everything but pre released updates

now u should be able to find the new version by searching semantic, but i think ubuntu already comes with glib so run the update manager first.


see if that will help you, sorry for the late post

---

