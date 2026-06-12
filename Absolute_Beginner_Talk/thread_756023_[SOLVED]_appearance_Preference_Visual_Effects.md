---
title: "[SOLVED] appearance Preference: Visual Effects"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ssdurn on 2008-04-15
Hi there

I'm trying to change the Visual Effects up to higher than basic. When it tried to get the 

NVIDIA accelerated graphics driver

 to do this I get the following message:

The software source for the package

   nvidia-glx

 is not enabled.

Any suggestions?

---

### Post by meborc on 2008-04-15
from [www.ubuntuguide.org](www.ubuntuguide.org) - >  NVidia Driver

First, determine what kernel you have running:

user@localhost:~$ uname -a
Linux localhost 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I have the generic kernel, so I need to install the following:

sudo apt-get install linux-restricted-modules-generic


After that's done, go to System > Administration > Restricted Drivers Manager and turn on the driver.

Some users may receive an error screen: "The software source for the packsge nvidia-glx-new is not enabled." This can be overcome by going to System > Administration > Software Sources and ticking all the boxes under the heading "Downloadable from the Internet", click close and then allow Ubuntu to reload the package lists. The NVidia drivers can then be enabled using the method above. 

There is a bit on your issue at the end

hope this helps

---

### Post by john91 on 2008-04-15
You probably just need to go to System > Administration > Software Sources and check all the main repositories and the Third-Party Software.  Then, update your repositories and it should work.


EDIT: too late :P

---

### Post by Inxsible on 2008-04-15
If you are using Gnome, you can also enabled restricted drivers by going to System>>Administration>>Restricted Driver Manager and check mark the box next to NVidia drivers. Restart the machine and then try to enable Effect on the System>>Preferences>>Appearance >>Visual Effects tab

---

