---
title: "Trying to install using synapic package manager?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-12
How come when i try to install things by synapic package manager it never does?

When i search for the program i want, it there but then when i mark for installation and apply changes, it just stays hanging!

Ive tried shutting down all other programs running while im attempting to do this but still no luck!

---

### Post by risbac on 2006-09-12
Maybe you have an update blocked or something like that. Did you try to open Synaptic, and simply update without installing anything? 

And you say "hanging". Do you see the popup window showing the download? Maybe there is a problem to contact the repositories, like a proxy, firewall, etc... 

So what I would do:

open a terminal, 

```
sudo apt-get update
``` 

and 

```
sudo apt-get dist-upgrade
```

This will  update your system. If you have error message for those two commands, please copy paste them here and we'll see.

If it's working, try 

```
sudo apt-get install name_of_the_package_to_install
```

You will find the name in Synaptic. 

Why a terminal? Coz usually you can see more error messages than with a GUI.

---

