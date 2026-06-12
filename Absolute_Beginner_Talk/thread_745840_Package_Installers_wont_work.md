---
title: "Package Installers wont work"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by hitspace on 2008-04-04
ive been getting an error mesage along the lines of " you already have synaptic running or some other error along tthat lin" my cpu is running at 100 percent even when i have no programs open and nothing running in the background . any suggestions ? 


there is another synaptic running same message every time so should i go to the package manager to shut it down ? ive already tried rebooting the same problem again and again

it also says dpkg interrupted  must manually run dpkg a to configure the problem ... what ?

---

### Post by PmDematagoda on 2008-04-04
Can you post the output of:-
```
sudo apt-get update
```

---

### Post by Rocket2DMn on 2008-04-04
Can you please post the error exactly?

---

### Post by hitspace on 2008-04-05
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

exactly as how it comes out of sudo apt get update


its says i need super user privledges to run dpkg --configure -a 

but i only have one account with one password so how do i get in ? my account is the admin/superuser right ?

---

### Post by Oldsoldier2003 on 2008-04-05
> **hitspace said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

exactly as how it comes out of sudo apt get update


its says i need super user privledges to run dpkg --configure -a 

but i only have one account with one password so how do i get in ? my account is the admin/superuser right ?

```
sudo dpkg --configure -a
sudo apt-get install -f
```

If you have any more error messages just post them here

---

### Post by paydaydaddy on 2008-04-05
open a terminal and then type in
```
sudo apt-get -f install
```
this will attempt to fix broken/interupted packages.
Then type in
```
sudo dpkg --configure -a
```
you may need to run more than once

---

### Post by linuxbeatswin on 2008-04-05
> **paydaydaddy said:**
> open a terminal and then type in
```
sudo apt-get -f install
```
this will attempt to fix broken/interupted packages.
Then type in
```
sudo dpkg --configure -a
```
you may need to run more than once

Thanks for this- I was having a bit of a problem, and this thread solved it for me. Hope it works for you, hitspace.

---

