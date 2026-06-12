---
title: "removing packages comletely"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-03-07
Hello, I've recently installed the Lyx package with the synaptic package manager  since i was searching for an appropriate tex editor. Now i find  that this one is not optimal for me and thus want to remove it completely. By installing Lyx syntpamanager told exactly on which packages it also depends on and so i installed all necessary (which are about 40), but now how do i now which packages to remove? This question is of general matter, since when installing programs, the package manager tells the dependencies, but by uninstalling it doesn't, furthermore it is possible, that another program p2, say, that was being installed later depends on a package x, that originally being installed for another program p1. If i want to uninstall p1 how do i know wether or not remove x?

---

### Post by ghanthar on 2006-03-07
Hi,
The easiest way as I know is:
1- Open Synaptic
2-From file menu click History
3-There along with Lyx you shoul see all the packages installed.
4-Remove them as you would usually
Another solution may be (not sure about this but it should work)
Use aptitude: 
```


sudo aptitude install lyx 

``` or 
```

sudo aptitude remove lyx

``` it should remove the package with all its dependencies.

---

### Post by stalefries on 2006-03-07
Also, after removing lyx, you could use deborphan to find out the leftover packages. It's not installed automatically, though.
```
sudo apt-get install deborphan
deborphan
```

That will print out all packages that are unnecessary. Remove whichever ones you want. Also, not that you may have to repeat this to get all of them.

---

### Post by kayas80 on 2006-03-07
[quote=stalefries]Also, after removing lyx, you could use deborphan to find out the leftover packages. It's not installed automatically, though.
```
sudo apt-get install deborphan
deborphan
``` 
That will print out all packages that are unnecessary. Remove whichever ones you want. Also, not that you may have to repeat this to get all of them.[/quote]

That's great cheers. It would be good if they could somehow add it to synaptic!

---

