---
title: "Removing xubuntu-desktop and all related packages"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-12-15
I've just been playing around with XFCE, and have decided that the difference in speed on this machine is small enough to stick with Gnome. I installed Xubuntu alongside Ubuntu with the xubuntu-desktop metapackage. How do I remove everything it installed?

---

### Post by Hex_Mandos on 2006-12-15
sudo aptitude remove xubuntu-desktop

---

### Post by happy-and-lost on 2006-12-15
It's not installed, apparently.

Must be because I unchecked the Usplash theme installation

---

### Post by xyz on 2006-12-15
Did you use 'aptitude' or 'apt-get' to install? Or how did you do it?
Also go here if you will:
[Check under "Playing around"]("http://www.psychocats.net/ubuntu/")

---

### Post by happy-and-lost on 2006-12-15
I selected xubuntu-desktop in Synapytc, allowed it to install dependancies and unchecked the Usplash (which also removes th metapackage)

---

### Post by bodhi.zazen on 2006-12-15
The (Ed,K,X)Ubuntu-desktop packages are meta packages and unless you installed with aptitude, follow the link below:


[How to remove (Ed,K,X)Ubuntu-desktop](http://doc.gwos.org/index.php/Install/remove_%28K%2CX%2CEd%29ubuntu-desktop_packages)

In addition see here: [Purge xfce](http://www.psychocats.net/ubuntu/puregnome)

Note: This is a potential advantage of aptitude over apt-get (Synaptic is a GUI front -end for apt-get).

Use:```
sudo aptitude install package-xyz
```

If you used aptitude, I am told:```
aptitude remove Xubutnu-desktop
``` would be ut to the task at hand.....

But I can not confirm that.

OFF TOPIC Hi XYZ :p

---

