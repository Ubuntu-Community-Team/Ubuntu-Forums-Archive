---
title: "gnome + KDE"
date: 2005-05-23
forum: Apple PPC Users
---

### Post by r1kk1 on 2005-05-23
Hi,

Have a g3 600 ppc ibook. 

Problem is that I want to run the kubuntu and ubuntu desktops.  I found a web site that stated:

"Using synaptic, choose kubuntu-desktop, install, logout, choose kde and log back in."  Problem is that it justs hangs.  It did prompt me during an install if I wanted to use gdm or kdm but I thought kde can use gdm as well as kdm.

What is missing?

I can triple boot no problems but can't for the life of me figure out how to get kde and gnome to coexist without some fancy work around.

thanks,

eric

---

### Post by SGC on 2005-05-23
Does it hangs when you try to login or when you choose between KDM and GDM ?

If the problem is in the display manager then try to change it by running one of the following commands:
dpkg-reconfigure kdm
dpkg-reconfigure gdm

also while in Gnome try to run KDE to make sure it is installed, by running the following command:
startkde

---

