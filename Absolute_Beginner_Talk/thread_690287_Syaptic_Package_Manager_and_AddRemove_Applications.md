---
title: "Syaptic Package Manager and Add/Remove Applications"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by porlaizquierda on 2008-02-07
When I open the Synaptic Package Manager for 7.04 I get this message:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Then when I try to open the Add/Remove Applications I get this.


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

And when I type in both of those commands into the Terminal I get:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

What do I need to do? Please help me.

---

### Post by taurus on 2008-02-07
I guess you tried to add medibuntu repos but somehow screwed it.  Therefore, you should consider removing it.

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by PmDematagoda on 2008-02-07
Remove the file causing the problem using:-
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
and then execute:-
```
sudo apt-get update
```
That should fix your problem.

---

### Post by porlaizquierda on 2008-02-11
Thank you so much! Everything works perfectly now.

---

