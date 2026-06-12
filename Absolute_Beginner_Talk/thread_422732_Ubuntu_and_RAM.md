---
title: "Ubuntu and RAM"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by bosshoof on 2007-04-25
hi 
can i make the system less dependent on RAM
and make it more dependent on the swap space i assigned for it ?

thanks in advance

---

### Post by trippinnik on 2007-04-25
Why would you want to do that?  It'll make your computer much much much slower....

---

### Post by tennyis on 2007-04-25
> **bosshoof said:**
> hi 
can i make the system less dependent on RAM
and make it more dependent on the swap space i assigned for it ?

thanks in advance

Like the previous poster said it is going to make the system run slower.. Unless you have some crazy low amount of ram, but setting the value to 100 will do what you're asking... 

Source: [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.
Tweak

    * First we have to gain access to your /etc/sysctl.conf file. 

sudo gedit /etc/sysctl.conf

    * Just scroll to the bottom of the page and add the tag listed below. The number you want depends on how much ram you have and what you do with your system. Please read the about above this to make your decision. I have mine set to 0 on a dual core laptop with 1 gig of ram and have seen no issues and a good performance gain. 

vm.swappiness=0

And you're done.

---

### Post by bosshoof on 2007-04-25
as my RAM isn't high
and doesn't swap space act as RAM for the system?

---

### Post by oilchangeguy on 2007-04-25
if you've got a computer that needs to use swap/virtual memory, you've got a computer with problems. increasing your computers ram is your best bet. not decreasing it.

---

### Post by tennyis on 2007-04-25
The purpose of the swap file is to use it when your system is running low on ram. On a system with low memory, setting it to use the swap file more will just mean that you will use less of the ram that you do actually have.

---

### Post by trippinnik on 2007-04-25
How much memory do you have?  Getting more memory is your best bet as mentioned before, but you could try some lightweight Window Managers (GUI Interfaces).  IceWN, Fluxbox, e17 Enlightenment, xFce to name a few.

---

