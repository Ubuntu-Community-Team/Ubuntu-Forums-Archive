---
title: "Installing Troubles"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by browserjoe on 2007-06-01
Not Ubuntu, but everything I downloaded and tried to install so far (updates, limewire, etc.) I click "install package" but it keeps saying:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a'to correct the problem 
E:_cache->open() failed, please report."


Does "E:" mean the HD partition? because I know for a fact E is my windows XP partition, Im not completely sure what Ubuntu is, but I think It is C:



Also, my GFX card is 8800GTS, where can I download the appropriate drivers for it?

---

### Post by taurus on 2007-06-01
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by drowner on 2007-06-01
> **browserjoe said:**
> Not Ubuntu, but everything I downloaded and tried to install so far (updates, limewire, etc.) I click "install package" but it keeps saying:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a'to correct the problem 
E:_cache->open() failed, please report."


Does "E:" mean the HD partition? because I know for a fact E is my windows XP partition, Im not completely sure what Ubuntu is, but I think It is C:


Also, my GFX card is 8800GTS, where can I download the appropriate drivers for it?

no, E: is telling you there was an error

Linux doesn't work with E:, C: etc. It doesnt exist.

---

### Post by browserjoe on 2007-06-02
Now Im getting another message:

"It is impossible to install or remove any software.  Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue first"

---

### Post by zvacet on 2007-06-02
In terminal

```
sudo apt-get install -f
```

---

### Post by browserjoe on 2007-06-09
> **zvacet said:**
> In terminal

```
sudo apt-get install -f
```
I do that but then terminal says:
```
pm5k8135@pm5k8136:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

So I run dpkg --configure -a and it says:
```
pm5k8136@pm5k8136:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
pm5k8136@pm5k8136:~$ 
```

And I'm the only user on this comp, how do I make myself a superuser?

---

### Post by Trueno22 on 2007-06-09
sudo dpkg --configure -a

---

