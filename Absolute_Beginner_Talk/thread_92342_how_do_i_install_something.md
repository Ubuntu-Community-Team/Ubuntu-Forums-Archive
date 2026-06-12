---
title: "how do i install something???"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by dark_mage93 on 2005-11-19
hi i'm kinda new to linux/ubuntu....i was wondering with this distro, how exactly do you install a .tar file or whatever...i think i need to put it in a certain directory and be root, then do like 
./configure && make
make install
then it should work but it doesn't 
i'm trying to install tor on a NEC pentium 2 laptop

---

### Post by Jussi Kukkonen on 2005-11-19
in command line:
```
sudo apt-get install tor
```
or graphically open Synaptic (system/administration/synaptic), and find "Tor" there...

(edit:) I just noticed Tor is only in the "universe" software repository, so you'll need to enable that repository first. See [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) for instructions.

---

### Post by dark_mage93 on 2005-11-19
Thanks!!!

---

### Post by Nolochemical on 2005-11-19
Umm will this get an install file from a cd, internet, ...?

I have this code to install Fluxbox :
```
 sudo apt-get install fluxbox fbdesk fbpager fluxconf 
```

I wanted to install Fluxbox I have the commands,but I'm at a loss..I dont know how to install it from the ubuntu cd's.:???:

---

### Post by Kvark on 2005-11-19
[QUOTE=Nolochemical]Umm will this get an install file from a cd, internet, ...?[/QUOTE]
Look at the file /etc/apt/sources.list to find that out. If there is a line that says something about cdrom and is not commented (lines that start with # are commented which means they are ignored by computer programs) then it installs from both the cd and internet. Otherwise it installs only from the internet.

---

