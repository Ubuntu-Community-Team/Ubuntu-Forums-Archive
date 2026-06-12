---
title: "linux-restricted-modules-2.6.22-14-server"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by sirtah on 2007-11-23
I'm running the gutsy server edition with the gnome GUI but I'm unable to access the restricted drivers manager and when I attempt to I get the following error" 

----
You need to install the package 

linux-restricted-modules-2.6.22-14-server

for this program to work. 
----

I cannot seem to find a solution to this problem anywhere. Suggestions? 

Thanks.

---

### Post by wirelessmonkey on 2007-11-23
Install the package. :)

From terminal:
sudo apt-get install linux-restricted-modules-2.6.22-14-server

From Synaptic, if you prefer, just search for linux-restricted-modules, and choose the correct one from the list.

---

### Post by sirtah on 2007-11-25
Thanks for your response but I don't think the package exists. When I run 

sudo apt-get install linux-restricted-modules-2.6.22-14-server

I get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.22-14-server

I did a basic Google search and read some threads including 
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/153011](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/153011)

but I'm running an ATI card not nvidia 

Thoughts?

---

