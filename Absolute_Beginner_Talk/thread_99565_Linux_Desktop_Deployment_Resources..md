---
title: "Linux Desktop Deployment Resources."
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by taugust04 on 2005-12-05
Hello,

I was wondering if anyone can point me in the right direction of some resources and tools for deploying Ubuntu in a computer lab environment.  For example, where I work, we use Ghost for creating and deploying Windows images, and a free software product called NetRestore for deploying Mac OS X software images.

There is some interest in Linux, but my supervisors won't budge on it being deployed until I have some resources for it being in our environment.

I am also looking for some resources on how to build a customized Linux image.  Again, I will use Windows as an example, where you can create a user account with the settings you want all users to receive, and then copy it to make it become the "Default User" (On the Mac its the "User Template").

Thanks in advance for helping out a newbie!  I really want to have Ubuntu as an option for our computer users.

---

### Post by bluefrog on 2005-12-06
you can make images with a cd called systemrescuecd and the program partimage which is on the cd. You can also use partimage from a ubuntu live cd (you have to install it though on a live CD before using it).

Partimaged is the server side meaning you can make / asve /restore images to /from the network.

/etc/skel is the place where you can have all users get their default profile. In theory. I say that because all I have been able to find about /etc/skel on the internet is theory. No one have been able to provide me with a working example so far. And the way to use it in gnome desktop is a wee bit tricky (at least for me).
You can use a program called sabayon to create and then allocate profiles to users. But it needs human interaction.

The really neat way to allocate profile is by creating a default profile and put it in /etc/skel. Furthermore creating different profiles and putting them in /etc/skel1, /etc/skel2 ... would be a way to allocate default profile to people depending on groups membership.

Community help welcomed on how using /etc/skel properly.

James

---

