---
title: "Some questions about dependency and Python"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mocqueanh on 2007-06-13
I dont understand about conflict and Replace in the Properties of packs i see in Synaptic,
Example:

[img]http://img223.imageshack.us/img223/7158/screenshotcdrecordpropeaf2.png[/img]

I see the suggest is: xcdroats
But the conflict is: xcdroats, why ?

And what the "replaces" mean ?


The second question: my Ubuntu 6.1 is default Python is a version 2.4
I download version 2.5 from Internet ( dont have internet access at home, so i download to USB ), and install on my Ubuntu, after type:

./configure && make && sudo make install

Then terminal say: i've installed it. But when i see in Synaptic, my Python version is still: 2.4, and the apt-cache show command say too.(before install 2.5, i didn't remove the version 2.4 ).

Can you define for me ?:(

---

### Post by mlentink on 2007-06-13
I am afraid I can only answer your last question. 

When you install from source, you do not go through the apt system. Synaptic, aptitude etc. are all using the apt-system, including the registration of packages installed through it. 
Since you installed outside of the apt-system, your installation was never registered within it, and therefore it does not show.

Does this help?

---

### Post by mocqueanh on 2007-06-13
So, i must have internet access to upgrade packages on my system ?

---

### Post by mlentink on 2007-06-13
No, you dont need internet access per se, although I would highly recommend it because it makes your life a lot easier. You have upgraded your Python version, it just does not show up in apt (and therefore not in aptitude or Synaptic). 
Perhaps, if you are or have been a windows user, you can compare it to the registry. Some programs do not use that registry at all, and will not show up in the windows add/remove software list.

---

### Post by mocqueanh on 2007-06-13
Ah, understood, thank you

---

