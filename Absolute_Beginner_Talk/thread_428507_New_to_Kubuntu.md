---
title: "New to Kubuntu"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by goldenatom on 2007-04-30
I've been using Ubuntu for a while now and wanted to give Kubuntu a try. I thought it wouldn't be all that different, but I've run into a few problems already. The main problem (for now) is that I can't seem to install .deb files. I tried to install Kmymoney and Automatix2 from the .deb files, but I kept getting dependency errors. In Ubuntu the needed packages were just downloaded and installed...how do I do this on Kubuntu.

---

### Post by taurus on 2007-04-30
If you plan to install .deb by hand, then you need to hunt down and install all the dependencies yourself.  But if you install it through synaptic/apt-get/aptitude, then the system will install all the dependencies for you.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by adamklempner on 2007-04-30
To get automatix to install in Kubuntu 7.04 I did this:

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt)

But on the last step I had to add the "-f" to make it install all of the dependencies:
> sudo apt-get install -f automatix2
It seems as if automatix depends a ton of gnome stuff...

---

