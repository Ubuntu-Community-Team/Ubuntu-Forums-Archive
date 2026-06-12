---
title: "Bit confused about apt and Synaptic"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-07-15
On one of my posts in the forum I was told that I shouldn't 
mix and match different package managers. (talking about apt-get,synaptic and aptitude).
On another post somebody told me that apt-get is the same as using synaptic (just a gui).

So, what is the truth? What should I do? Can I use both apt-get and Synaptic or should I just stick to synaptic?

*I have probably misunderstood something that the other memebers of the forum told me. I am not saying they told me something wrong and apoligise if I have tweaked their sayings.*

---

### Post by bukwirm on 2006-07-15
I have not had any trouble using a combination of different package managers (aptitude, apt-get, and Synaptic).

---

### Post by ahaslam on 2006-07-15
Synaptic is basically a GUI for apt-get. Aptitude is similar to apt-get but can offer a cleaner uninstall as it removes any dependencies that it added during installation. Some may consider the last point as a drawback if many things have been installed (dependencies may now be used for another app).

Tony.

PS. I also haven't experienced any problems in mixing these techniques. Some are simply better in different situations.

---

### Post by az on 2006-07-15
All packages manager lock the package database while they are running so that they do not do evil things behind each others back;  you cannot run two at the same time.  You can't even run two apt-get commands at the same time - the first one will have the lock until completed.


As for repositories, do not mix non-ubuntu repositores with the ubuntu ones.  For example, don't add a Debian repo to your list becuase you want one package - you will bork your package manager.

But you can install somethign with aptitude and another thing with apt-get and your system will be happy.  All of the package managers use dpkg which uses the same database.

---

### Post by geokok1981 on 2006-07-16
well, I 've only added one extra repo, the one required to install automatix....should I remove it?

---

