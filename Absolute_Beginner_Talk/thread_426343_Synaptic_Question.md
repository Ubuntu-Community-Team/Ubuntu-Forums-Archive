---
title: "Synaptic Question"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by k5ilf on 2007-04-28
When I install files from Synaptic, where will I find them? The system indicates that they are installed, however I cannot find the files---what am I doing wrong?

bill in las cruces:confused:

---

### Post by taurus on 2007-04-28
Most of them are in /usr/bin.  You can also run them from a terminal, Applications -> Accessories -> Terminal.  What apps did you install using synaptic?

---

### Post by AlexenderReez on 2007-04-28
> **k5ilf said:**
> When I install files from Synaptic, where will I find them? The system indicates that they are installed, however I cannot find the files---what am I doing wrong?

bill in las cruces:confused:

it is in /var/cache/apt/archives ....

open to configure 
> sudo nautilus

---

### Post by mgmiller on 2007-04-28
If you installed an application, just look around in your Applications menu for the icon to launch it.  Some times, you can only run a utility from the command line, open a terminal and try typing the first few letters of the command and then hit tab to see what your choices are.  Once you figure that out you can add it to your applications menu from System>Preferences>Main Menu.  

It you want to see where all the files went, go back into synaptic and search for the package again.  When you  find it, high lite it and then right click and select properties.  Go  to the installed files tab and you will see where it put everything.

---

