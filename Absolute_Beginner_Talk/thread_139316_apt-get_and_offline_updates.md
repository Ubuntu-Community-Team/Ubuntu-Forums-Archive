---
title: "apt-get and offline updates"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by garner_nc on 2006-03-03
Is it possible to use apt ( or synaptic) to download packages, with dependencies, and copy them to a CD for installation to another, stand-alone, non-networked, machine? I've been trying to install some games on my sons machine but keep running into dependency problems.

All the best
Doug White

---

### Post by joshuapurcell on 2006-03-03
When you select packages to install using Synaptic and click 'Apply', there is a checkbox that you can select on one of the following windows that allows you to only download the packages rather than install. Once they are downloaded you can copy them wherever you want and install them other places if needed.

---

### Post by garner_nc on 2006-03-03
Thank you Joshua. Now, what directory are these packages downloaded to?

All the best,
Doug White

---

### Post by joshuapurcell on 2006-03-04
I believe it is in /var/cache/apt/archives/ (since that is where many of my .deb files are located). You can do a search on your system for the package you downloaded through these commands:```
sudo updatedb
locate nameOfPackage.deb
```.

---

