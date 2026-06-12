---
title: "adept not working"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by darkside299 on 2007-01-21
I have installed Kubuntu 6.10 2days ago. Earlier i was using the 6.06 version. In both the cases i could not update my PC software. Also when i start adept it shows only installed packages and does not show packages which are not installed. I am not able to install any packages directly by using dpkg as it always has the dependency problem. I have also tried apt-get which is also not working.

I have windows XP installed along with kubuntu. 
Configuration : pentium 4 with 3.0GHz. Motherboard 865GBF, 512 RAM, LAN card DFE 520TX, 80 GB Segate Hard disk.

what should i do to solve this problem?
Is there any other way to install various softwares without dependency problem?

---

### Post by rabid emu on 2007-01-21
Have you tried aptitude?  That's supposed to be better at resolving dependencies than apt-get.

---

### Post by darkside299 on 2007-01-21
I have tried aptitude. The same problem persists. 
It gives the following error message:

could not connect to archive.ubuntu.com:80, connection timed out

Even in case of adept whenever i ask to fetch updates, it starts the download. but gets stuck at 0%.

What is the problem with my PC?

---

### Post by CroEragon on 2007-01-21
A firewall issue?
Or, DNS?
Can you browse web?

---

### Post by darkside299 on 2007-01-24
No. It wasnt a firewall issue.
Yes i mean "was".

There was a problem with the repository list which contained entries for repository that did not exist(or may be r obsolete). I have changed it.
Now it is working propely

---

