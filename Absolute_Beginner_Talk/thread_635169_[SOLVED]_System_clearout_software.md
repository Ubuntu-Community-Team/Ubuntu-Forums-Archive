---
title: "[SOLVED] System clearout software?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2007-12-08
hi,

On my windows pc, i use software called ccleaner to clean out the computer of unneaded files etc. and save space.

on my ubuntu pc i have a very small hard drive (20G), and something similar would be useful....

also, is there anything that removes unneaded packages (e.g. if I install something that installs loads of other pagages or dependancies or whatever....and i then uninstall it, but it doesn't remove those extra packages)

thanks for ya help

---

### Post by taurus on 2007-12-08
Applications -> Accessories -> Terminal
```
sudo apt-get clean
```

---

### Post by benji.ijneb on 2007-12-08
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get clean
```


what does that do?

---

### Post by CatKiller on 2007-12-08
> **benji.ijneb said:**
> what does that do?

From **man apt-get**:

>        clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           _/var/cache/apt/archives/_ and _/var/cache/apt/archives/partial/_. When
           APT is used as a **dselect** method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.


---

### Post by benji.ijneb on 2007-12-08
> **CatKiller said:**
> From **man apt-get**:

nice. how much space should that clear out?

---

### Post by CatKiller on 2007-12-08
> **benji.ijneb said:**
> how much space should that clear out?

It depends entirely on how much you've installed. My /var/cache/apt is only some 30 megs, for example, but I cleaned it a couple of weeks ago and I haven't really installed that much recently.

All of the little things, like apt-get clean and removing the contents of your ~/.thumbnails directory, can be done as **cron** jobs scheduled for every couple of weeks or so so that you don't have to remember to do it every time.

It's worth remembering that **aptitude** and the later versions of **Synaptic** - like the one in Gutsy - automatically remove packages if nothing depends on them and the package that led to them being installed automatically is removed. **apt-get** doesn't, as far as I know.

---

### Post by fineas on 2007-12-08
> **benji.ijneb said:**
> nice. how much space should that clear out?

It will clear out as much space as it is the files that CatKiller listed. 

CCleaner cleans some registry things (this cannot be done in ubuntu as there is no registry), recycle bin (you can do it manually), temporary files (most of them are in /temp directory and are cleared automatically during shutdown), recent documents (you can do this manually0 and cookies (don't know a general method, but each web browser includes a relevant function)

---

### Post by Bruce M. on 2007-12-08
> **benji.ijneb said:**
> nice. how much space should that clear out?

That would depend on what you have installed, etc etc.
--------------
ccleaner is "almost" a requirement with Windows, because of the junk files collected over time.  Linux isn't "so" prone to this.

ccleaner is mostly used to clean out cookies, history files, viewed doc lists etc.
--------------
This is not what " sudo apt-get clean " does. ( If I am in error someone please correct me. )

If you are concerned about space another thing you can do is open Synaptic Package Manager

System>Administration>Synaptic Package Manager

then:

Settings>Preferences>Files

and -check- "Delete downloaded packages after installation"

This is equivalent to deleting ZIP files in Windows after you use them to install the programs.
-------------------

BTW:  that "sudo" in the command 

```
sudo apt-get clean
```

applies "Admin" rights to the command that follows.  Use it with care.

see the manual (man = manual) in Terminal:

```
man sudo
```
------------------

If you are worried about files being left behind after deleting a program you had installed earlier then you could get: GtkOrphan

System>Administration>Synaptic Package Manager

then:

Search:  GtkOrphan

A graphical tool to find and remove orphaned libraries
GtkOrphan is a graphical tool which scans your debian system, looking for
orphaned libraries. It implements a GUI front-end to deborphan, but adds the
package removal capability.
A detailed documentation on the program can be found at:
[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html).

(Ubuntu is a debian based system)

As for cookies:  Firefox (or the browser of your choice) and in preferences tell it to delete cookies when you close the program.

Hope this helps.
Welcome to Ubuntu

---

### Post by benji.ijneb on 2007-12-08
thanks everyone so much, this has been really helpful, also, i found this, 
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
 which does the job nicely

---

