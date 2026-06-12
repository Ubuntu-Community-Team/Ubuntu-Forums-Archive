---
title: "My god I am lost please help me haha"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ch33ch00 on 2008-02-23
As you could probably gather from the title I am a Linux virgin, haha. I am having 2 problems,

The first being, when I try to install updates i get the following message:  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


No idea what to do here some help would be great.

The second problem I am having is, when I try to install a new program I get the following message:

Only one software management tool is allowed to run at the same time: Please close other application eg`Update manager', 'aptitude', or 'Synaptic' first.

Again not sure what to do here.

Any help that I can get will be greatly appreciated

Thank you

---

### Post by taurus on 2008-02-23
1.  Close that update window and then open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

2.  You can only run Add/Remove, synaptic, or apt-get/aptitude one at a time.

---

### Post by lyceum on 2008-02-23
I would recommend using Add/Remove first, it is very easy. But, in my signature there is a link to a page that can walk you through installing. Just click on "Install Anything"

Good luck :)

---

### Post by candtalan on 2008-02-23
it looks like you need to clean up the package manager.

Ensure you are connected to the internet,
Open a terminal (looks like a dos window, but it is not....)

then type the following
sudo dpkg --configure -a

note the space following sudo
the space following dpkg and 
the space following configure

type your password when requested, then press return

when you have typed in the characters and checked for typos, press return and await the package cleanup. It may take some time.

good luck

---

### Post by ch33ch00 on 2008-02-23
That worked for me, Thank you for your help

---

### Post by steveneddy on 2008-02-23
> **ch33ch00 said:**
> That worked for me, Thank you for your help

Make sure you click the **Thanks** icon in the lower right of the post you want to thank. It looks like a star.

---

