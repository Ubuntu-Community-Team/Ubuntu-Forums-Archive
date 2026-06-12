---
title: "E: Couldn't find package"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-06-14
Hi folks,

I've been trying to download a few things (e.g., Wine, SynCE, etc.) but almost everytime I get the following error:

E: Couldn't find package tree


So, I decided to try to get something really simple, like tree. I typed the following:

sudo apt-get install tree

And got the following:

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tree
ben@ben-ubuntu:~$ 
[/HTML]

The thing is, when I go to System->Administration->Software Sources, All the boxes are checked except for "Source code" (which has a box with a minus sign in it). 

What am I doing wrong?

Thanks in advance.

---

### Post by FleetAdmiral74 on 2007-06-14
Hmm, do a quick search on multiverse and universe repositories, I know if I did not have them enabled in some config file I got this. Once these are added, you have to type something like sudo apt-get update or upgrade, something like that, and it always worked for me.

---

### Post by plinydogg on 2007-06-14
FleetAdmiral74: Do you mean search teh forums for multiverse and universe repositories? 

Thanks for your post!

---

