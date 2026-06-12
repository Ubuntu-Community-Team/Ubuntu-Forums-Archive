---
title: "need some help,new to Ubuntu..."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Sean14 on 2007-07-03
i tried to install automix2,than it messed up,now this is what it says when i try to add programs

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

can anyone help please?im only 14 lol:p

---

### Post by use a name on 2007-07-03
Hi!

I guess the package wasn't found?

I've checked my /etc/apt/sources.list and this is the automatix section:
```

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

```
You can edit the file by typing
```

sudo gedit /etc/apt/sources.list

```
into the terminal. (In case you're on Kubuntu: use kate instead of gedit.)

EDIT: After saving the file, you have to enter the two commands that were suggested.

Hope it helps!

---

### Post by hyper_ch on 2007-07-03
What did you want to use automatix for?

---

### Post by acowboydave on 2007-07-03
There is a post or thread out Beware of" automatix"

---

### Post by Malibu Illusion on 2007-07-03
I'd recommend against using Automatix to install things: it has the potential to damage your sources.list as it has done in this case and potentially install from questional 3rd party repositories.  Everything you can do with it can be manually achieved without much more effort, you'll learn something and have it installed properly without butchering things too.

In many cases, the programs that you're looking for are available in the official repositories also and can be installed with a simple apt-get install; no need for other 3rd party programs to interact with, imo.

---

