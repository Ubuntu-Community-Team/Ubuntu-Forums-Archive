---
title: "Gaining root privliges to edit config file..."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-12
I feel stupid asking this, it should be simple. 

So just a simple text file, what is the easiest way to open it with root? Do I need to use the terminal, or is there another method? I swore there was a keyboard shortcut, but I don't remember...

---

### Post by taurus on 2007-05-12
Applications -> Accessories -> Terminal
```
gksudo gedit **filename**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by FleetAdmiral74 on 2007-05-12
Neato, thanks for the quick reply!

Hmm, I still cant get the specific file. Its en the etc folder, privoxy, and then the file called config. I tried

gksudo gedit /etc/privoxy/config and the same thing just typing in the file name, but no luck, blank file comes up...

---

### Post by Iokua on 2007-05-12
It should also be noted that Automatix provides a script whereby you can right-click and select "gedit-root" to edit files as root. I use it all of the time, but keep in mind that these are third-party tools and are not supported by Ubuntu.

---

### Post by taurus on 2007-05-12
> **Iokua said:**
> It should also be noted that Automatix provides a script whereby you can right-click and select "gedit-root" to edit files as root. I use it all of the time, but keep in mind that these are third-party tools and are not supported by Ubuntu.

Why in the world would you want to install some 3rd party app (and could screw up your machine in the process) when you can just run it directly from a terminal?  ](*,)

---

### Post by FleetAdmiral74 on 2007-05-12
Never mind the above post, I had to point the terminal to the specific dir with cd before, I did not know that. Once i was in the privoxy dir gksudo gedit config worked.

---

### Post by Iokua on 2007-05-12
> **taurus said:**
> Why in the world would you want to install some 3rd party app (and could screw up your machine in the process) when you can just run it directly from a terminal?  ](*,)

What's the point of having a GUI if you can't use it? In my opinion, so long as editing conf files by hand is a necessity, a right-click option in Nautilus should be shipped by default. Besides, it isn't really an app, it's just a script. It's a small one too: 

```

#!/bin/bash
#created by arnieboy 
foo=`gksudo -u root -k -m "enter your password for gedit root access" /bin/echo "Do you have root access?"`
sudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS

```

---

### Post by 3rdalbum on 2007-05-12
It's not shipped by default, but it's available in the repos:

nautilus-gksu
...
Description: privilege granting extension for nautilus using gksu
 The gksu extension for nautilus allows you to open files with
 administration privileges using the context menu when browsing your
 files with nautilus.

---

### Post by Iokua on 2007-05-13
> **3rdalbum said:**
> It's not shipped by default, but it's available in the repos:

nautilus-gksu
...
Description: privilege granting extension for nautilus using gksu
 The gksu extension for nautilus allows you to open files with
 administration privileges using the context menu when browsing your
 files with nautilus.

Nice! I never knew that. Thanks!

---

