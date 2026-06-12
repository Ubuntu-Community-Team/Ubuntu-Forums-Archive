---
title: "About KDE Distro"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-19
Hello friends

I am using Ubuntu with the Gnome distro, just thought of switching to Kubuntu. Will the KDE distro take too much of system resource. i am gonna run it on a laptop so it does not have great resources (1.8 Ghz, 512 Mb , P4). So any comments will be much appreciated.

I quite like the KDE interface. Are there any significant disadvantages you could think off. And just curious if there is any other nice looking distro which i can look up :) 

Cheers for any help

---

### Post by gabruo on 2006-05-19
I find KDE to use only slightly more resources than GDM.  From your specs I think you have nothing to worry about...Give it a try, after all it is free and you can always go back to GDM or anyother you like.
Enjoy

---

### Post by hotbrainz on 2006-05-19
ya thats true, no harm in giving it a shot innit. thanks for the shout..

---

### Post by hotbrainz on 2006-05-19
ya thats true, no harm in giving it a shot innit. thanks for the shout..

---

### Post by macdo on 2006-05-19
When you install kubuntu, use aptitude: 
```
sudo aptitude install kubuntu-desktop
```
You'll find it much easier to uninstall if you decide that it's not for you. If you use apt-get or synaptic, you have to uninstall kubuntu packade by package, which is long and inefficient. Aptitude remembers what it installed and uninstalls the lot...
```
sudo aptitude remove kubuntu-desktop
```

---

### Post by Sef on 2006-05-19
When install Kubuntu to your Gnome, do it this way in your terminal:

sudo apt-get update

sudo aptitude install Kubuntu-desktop


It will be much easier to uninstall if you decide to do so.

---

### Post by hotbrainz on 2006-05-19
thanks a lot, will do it

---

