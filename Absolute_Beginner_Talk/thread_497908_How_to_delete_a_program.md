---
title: "How to delete a program"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by bamend on 2007-07-10
I installed peerguardian but it doesn't look like it's working.  How do you uninstall programs in Ubuntu?

---

### Post by MyR on 2007-07-10
in terminal:
sudo aptitude purge peerguardian

---

### Post by mr_byte on 2007-07-10
Assuming you used apt/adept/synaptic to install it, you can run a console and issue

*sudo apt-get remove peerguardian*

enter your password when prompted and that should do it.

---

### Post by establishment on 2007-07-10
OR you can go to Add or Remove Programs under Applications, Find the program on the list and un-check it.

---

### Post by bigboy_pdb on 2007-07-10
I don't know how you installed the program (that makes a difference). If you installed a package, you should be able to find it in Synaptic Package Manager (System -> Administration ->Synaptic Package Manager). Use "Find" to look for the program, right click it and click either "Mark for Removal" or "Mark For Complete Removal", and then click the "Apply" button.

---

### Post by MyR on 2007-07-10
if it's not a package, the uninstallation method should be in the documentation.
if none of these methods work, you'll just have to buy a new computer.

---

### Post by wolfen69 on 2007-07-10
by doing:
```
sudo aptitude update
```
then:
```
sudo aptitude remove <program name>
```
by removing with aptitude vs. apt-get, it will also remove any unused dependancies.

---

### Post by misfitpierce on 2007-07-10
I personally go under System -> Admin -> Synaptic Package Manager...
and search for program name then click box next to it and select uninstall completely!

---

### Post by PriceChild on 2007-07-10
> **wolfen69 said:**
> by removing with aptitude vs. apt-get, it will also remove any unused dependancies.Only if you installed with aptitude.

---

### Post by stchman on 2007-07-10
> **bamend said:**
> I installed peerguardian but it doesn't look like it's working.  How do you uninstall programs in Ubuntu?

If you installed with apt-get use:

sudo apt-get autoremove peerguardian

If you used aptitude then use:

sudo aptitude remove peerguardian

These will remove the programs and remove their dependencies.

---

### Post by stchman on 2007-07-10
> **wolfen69 said:**
> by doing:
```
sudo aptitude update
```
then:
```
sudo aptitude remove <program name>
```
by removing with aptitude vs. apt-get, it will also remove any unused dependancies.

apt-get autoremove also removes dependencies.

---

