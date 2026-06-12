---
title: "ubuntu file browser - admin"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-05
where do i enter the root password so when using the file browser i have those administrator access.... cant see anywhere ?

---

### Post by aktiwers on 2008-01-05
Open Terminal (applications => Accessories => Terminal) and type:
```
gksudo nautilus
```

Or download the zip I attached to this post, unzip it on your Desktop.

Then in terminal type:

```
cd Desktop
```
```
cp root-nautilus-here /home/YOURUSERNAME/.gnome2/nautilus-scripts
```

And change the YOURUSERNAME with your own username.

Then from now on, when you right-click there, you can pick "Scripts" and then "Root Nautilus Here".

Hope that helps.

---

### Post by kellemes on 2008-01-05
from terminal type: "gksudo nautilus"

---

### Post by mlentink on 2008-01-05
You could, for those activities where it is needed, start up nautilus with sudo. Open up a terminal and type:
```
gksudo nautilus
```

Do not forget to close that instance of nautilus when you are done

edit: whoops, beaten to it...

---

### Post by kellemes on 2008-01-05
> **mlentink said:**
> You could, for those activities where it is needed, start up nautilus with sudo. Open up a terminal and type:
```
gksudo nautilus
```Do not forget to close that instance of nautilus when you are done

edit: whoops, beaten to it...

edit: delete

---

### Post by nick_h on 2008-01-05
You may also wish to install the nautilus-gksu package.
```
sudo apt-get install nautilus-gksu
```
This will give you an "open as administrator" option on the right-click menu withhin nautilus.

---

### Post by waffler_87 on 2008-05-25
Hi, 

I'm a new Ubuntu user and seem to be having some serious problem.

The root filesystem within my ubuntu displays 'desktop configuration file' under the type heading. In search for a solution I came across this thread. In fact I was looking for a way to install the Gnosh player into firefox.
 
Anyway basically as I have tried to install nautilus, the following screenshot appears. I have attached a screenshot of the terminal window whilst executing the install.

Please can someone help me as it is the same problem for every single installation. If you require any further information please do let me know.

Regards

---

