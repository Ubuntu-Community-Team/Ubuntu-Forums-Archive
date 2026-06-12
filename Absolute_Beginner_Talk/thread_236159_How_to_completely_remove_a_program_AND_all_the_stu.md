---
title: "How to completely remove a program AND all the stuff it came with?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-14
I used synaptic manager to install "kchart". When I asked it to do that, it told me I had to install a few other things too. So I did, just following its prompts. Now I wanted to remove it so I did the "completely remove" thing for kchart. But I am wondering about those other things that went with it. They must I guess still be lurking in my system, quite uselessly. I have no idea of thei names. How can I get rid of them?
Thanks
Justin.

---

### Post by Ramses de Norre on 2006-08-14
Use aptitude in the future, that's command line but it'll take care of removing unused dependencies.
So ```
sudo aptitude install package
``` to install and ```
sudo aptitude purge package
``` to totally remove (including dependencies).
Use synaptic or ```
aptitude search keyword
``` to search for the package name.
For now: Use [http://packages.ubuntu.com/package_name](http://packages.ubuntu.com/package_name) to see what the dependencies are and remove them (you best use command line for extended output), be careful and don't continue when you get errors, that means another program is also using the dependency you want to remove.

---

### Post by jimmygoon on 2006-08-14
If you used Synaptic then you probably have orphaned dependencies laying around, luckily there is a package that removes that!!!

Its called "deborphan" I believe

---

### Post by true_friend on 2006-08-14
i also observed when i uninstall a software and then reinstall it, the files are not downloaded again. it means the package files are there in disk getting space. how to remove them.
i do all installations throuhg synaptic usually.

---

### Post by bruce89 on 2006-08-14
> **true_friend said:**
> i also observed when i uninstall a software and then reinstall it, the files are not downloaded again. it means the package files are there in disk getting space. how to remove them.

```
sudo apt-get clean
```
> **woodlandjustin said:**
> I used synaptic manager to install "kchart". When I asked it to do that, it told me I had to install a few other things too. So I did, just following its prompts. Now I wanted to remove it so I did the "completely remove" thing for kchart. But I am wondering about those other things that went with it. They must I guess still be lurking in my system, quite uselessly. I have no idea of thei names. How can I get rid of them?
Thanks
Justin.
Are you using KDE?  There is a program called gtkorphan which allows you to remove packages completely, but it is for Gnome.

---

### Post by Jucato on 2006-08-14
If you installed it through Synaptic, you will have a sort of a "log" that tells you what were installed and when. Open up Synaptic, the in the File menu, choose History. Then you can search for "kchart" and see what was installed along with it.

---

### Post by aysiu on 2006-08-14
Use *aptitude* from now on:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Barring that, use *deborphan* (command-line) or *gtkorphan* (graphical) to find and remove the "orphaned" packages.

---

### Post by true_friend on 2006-08-15
aysiu: aptitude is in graphical mode also now???
i try it.
where are these packages put in system. i may want to write a cd for these packages so not to waste my time next when i reinstall system.

---

### Post by aysiu on 2006-08-15
I don't think it's in graphical mode now, unless you count the text-mode GUI as "graphical."

Typing ```
aptitude
``` will give you the text-based graphical mode, but that mode just confuses me. I prefer to do something like ```
sudo aptitude update
sudo aptitude install *programname*
```

The packages downloaded by Synaptic, Adept, *apt-get*, and *aptitude* are download to the /var/cache/apt/archives directory.

---

### Post by Jucato on 2006-08-15
The Aptitude GUI (I think it's ncurses?) is even worse than Adept's. But I think it's the only "easy" way you can turn of Aptitude's "install recommends" option (otherwise you have add "-R" to every install command you do).

Btw, using "aptitude" will only launch the GUI in normal user mode. You can't do anything there except to browse packages. You still have to use "sudo aptitude" to make it run properly.

---

### Post by magnoliablossom on 2006-08-18
I installed tight vnc so a friend of mine could look around at my desktop but neither he nor I could figure out how to use it in Linux.  When I uninstalled it, it still left hidden folders of it all over the place and using:

> sudo apt-get autoclean

didn't touch them.  they're still there.  how do you get the hidden stuff?

---

### Post by Jucato on 2006-08-18
I don't know about apt-get, but in aptitude, i would use
```
sudo aptitude purge <package>
```

---

