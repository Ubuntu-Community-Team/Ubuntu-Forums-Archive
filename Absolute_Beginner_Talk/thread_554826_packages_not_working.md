---
title: "packages not working"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Greengrangroon on 2007-09-19
I'm afraid that no one will be able to answer this with such little info. Anyway:
Since last week every time I install something new nothing happens, the new program doesn't appear in "applications". It used to work fine. 
Anybody knows what it could be?

---

### Post by jamvegan on 2007-09-19
I assume that you're using either Synaptic or Add/Remove Applications?  Try installing something with apt-get and it should give you error messages that you can post here.

Open a terminal (Applications->Accessories->Terminal) and type:
```
sudo apt-get install packagename
```
where you replace "packagename" with an actual package name, of course. :-)  Enter your password when prompted.

---

### Post by Jeroen Vernooij on 2007-09-19
Hi,
Try to open a terminal and enter the name of the package you installed.
Example: You installed azureus but it doesn't show up in the menu.

Open a terminal and type:
```
azureus
```
and see what happens.

---

