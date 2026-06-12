---
title: "Synaptic  problem"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by Cud on 2005-10-19
Help! Synaptic wants to kill Hoary!!! 
I tried to compile flight gear and had an unsuccesful install of libc6 >02.3.2.ds1-21 and lib gcc1 and fgfs base >0.9.8 . Before I had tried to install flightgear version 0.9.4 directly from synaptic which was also unsuccesful, due to dependency problems. When I restarted Synaptic I got an error telling me to fix 3 broken packages. So I did, and then was about to apply some other (minor) changes that I made when I read the fine print and saw that synaptic wants to

apt (essential) will be removed
dpkg (essential) will be removed
sysvinit (essential) will be removed
acroread will be removed
acroread-plugins will be removed
alien will be removed
amule will be removed
anacron will be removed
apt-utils will be removed
aptitude will be removed
aspell will be removed
aspell-bin will be removed
aspell-en will be removed
at will be removed
base-config will be removed
console-common will be removed
console-data will be removed
console-tools will be removed
cupsys will be removed
cupsys-bsd will be removed
cupsys-driver-gimpprint will be removed
cupsys-driver-gimpprint-data will

and so on... a total of 190 packages, including 3 essential packages.

What did I do??
What Can I do?
Thanks

EDIT-
It seems to be the broken packages Libgcc1, Libstdc++6, and Flightgear 0.9.8-3. When I mark them for removal synaptic tells me that the chosen action affects other packages, and then presents me with the list of 188 other packages. Still clueless as to how to solve this problem.
Any help greatly appreciated.

---

### Post by towsonu2003 on 2005-11-24
did u manage to fix this? looks like you'll need a fresh  instal?? linux sometimes gets boring with dependencies but whatever.. I will later install another ubuntu on this HDD (replace dual boot winxp) as my testing system...

---

### Post by Cud on 2005-11-29
Thanks for the reply..
I "fixed" it by using dselect, and reinstalling the hoary update of libc6.

---

