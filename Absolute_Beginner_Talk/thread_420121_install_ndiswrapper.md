---
title: "install ndiswrapper"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Syngensmyth on 2007-04-23
I must be missing something basic.
When I try to install anything from the hd I get errors.
for example from the terminal I do
sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
it does not work, can't remember messages

from synaptic the error is
Dependency is not satisfiable:ndiswrapper-common

I did just find that I may need to run 2 commands:
sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all.deb
sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

I have not had a chance to try this yet.

I am trying to get my old DWL-G650 to work. Ubuntu recognizes the chipset and even sends/receives a small portion of data at startup but I can find no way to connect.

Thanks

---

### Post by meborc on 2007-04-23
you can run also this command```
sudo dpkg -i ndis*
```
this will install all .deb files with the starting "ndis"... so if you have more then 1 ndiswrapper package, you can install them all at once

---

### Post by Syngensmyth on 2007-04-23
AAHH, wild card, thanks, I'll try it. Haven't used command prompt much since old dos days.

So each deb package has 2 or more installs? How does one tell what they are with each package?

---

