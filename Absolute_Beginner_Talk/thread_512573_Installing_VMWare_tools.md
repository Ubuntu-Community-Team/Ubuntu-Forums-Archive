---
title: "Installing VMWare tools"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by dzldriver on 2007-07-29
Ok.  So here is where I am at.  I have had to install Ubuntu 7.04 Feisty Fawn in a virtual machine so as not to upset the domestic balance of my house.  :) Trying to install VMWare tools is proving to be a challenge though.  Everything is going great until I get to the point where the install script asks for the location of the running kernel.  I used 'uname -r' to find out that I am running 2.6.20-16-generic kernel.  When the machine asks me for the location I tell it and the following is the response that I get in the terminal window.
===========================================================
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-16-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

===========================================================

Does anyone know where I need to go from here.  I have been more or less forced away from the Linux world for the last two years.  The last OS that I tried to convert my family to was Mandrake 10.0.  I was not successful.

Hoping someone can help me.
dzl

---

### Post by dzldriver on 2007-07-29
I guess I should have mentioned that I am running VMWare 5.5.1.

---

### Post by scott.j on 2007-08-31
I had the same problem. See the link provided below.

The patch worked fine for me. I'm also running 2.6.20-16-generic kernel, but on vmware server 1.03.

This solution seems like the (?only) / best solution for the present.

Good luck.


[URL="http://tuxx-home.at/cmt.php?article=/2007/06/29/T12_33_53/index.html"]

---

