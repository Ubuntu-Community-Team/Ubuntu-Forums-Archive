---
title: "Synaptic Package Manager"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by IYA290 on 2007-05-18
Okay, so I was installing a package using the package manager; however, there was a short power outage and the computer turned off while in the middle of installing a package. Now when I try and use the synaptic package manager it says en error occurred and to do something manually. I ask for someone to guide me through whatever it asks for me to do. :confused:

---

### Post by bobplano on 2007-05-18
what was the error exactly and what did it tell you to do?

---

### Post by IYA290 on 2007-05-18
Here is what is says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by aysiu on 2007-05-18
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo dpkg --configure -a
```

---

### Post by alienexplorers on 2007-05-18
run from terminal:

> sudo dpkg --configure -a

---

### Post by IYA290 on 2007-05-18
Ok, I typed that and here is what I got:

irving@irving-desktop:~$ sudo dpkg --configure -a
Setting up beryl-plugins-data (0.2.1-0ubuntu2) ...
Setting up libberylsettings0 (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up libberyldecoration0 (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up beryl-core (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up beryl-plugins (0.2.1-0ubuntu2) ...
Setting up beryl-settings-bindings (0.2.1-0ubuntu1) ...

Setting up beryl-settings (0.2.1-0ubuntu1) ...
Setting up beryl (0.2.1.dfsg+git20070318-0ubuntu2) ...
irving@irving-desktop:~$ 

Is the problem fixed?

---

### Post by aysiu on 2007-05-18
Looks fixed to me.

By the way, in the future, copying and pasting is probably better than retyping for terminal commands.

---

