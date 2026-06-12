---
title: "Why not use &quot;sudo aptitude&quot; for all installs/uninstalls?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Henrythewound on 2006-07-05
Hey there, Im new to all this, but it seems when I ask questions about installing something new on my ubuntu drive I am usually told to use aptitude to install programs in lieu of the package manager as later removal is easier this way. My question is, why would you use the package manager at all if this is the case?

It seems as though using the package manager to install/uninstall programs can be messy as evidenced in [this]("http://psychocats.net/ubuntu/puregnome.php") link. The aptitude uninstall is much cleaner.

So, why not use aptitude for all installs? Is it more dangerous in terms of screwing up your system? Also, whats the difference (if any) between the following commands?

sudo aptitude remove offending_program

and

sudo aptitude purge offending_program

Thanks,
Joe aka Henry

---

### Post by T700 on 2006-07-05
Other than careless habit, I try to use it at all times.  Particularly with large, complex, packages, aptitude can really make removal much less painful.

Paul

---

### Post by aysiu on 2006-07-05
I don't know the difference between *remove* and *purge*, but [I've been advocating for a long time that people use *aptitude* instead of *apt-get* or Synaptic.](http://www.ubuntuforums.org/showthread.php?t=164082)

Synaptic Package Manager, of course, has a nice graphical frontend that's new-user friendly, but in terms of package management, *aptitude* is better, of course.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

I will sometimes find myself using Synaptic to search for certain packages when *apt-cache search* isn't doing it for me. But then I'll use *aptitude* (not Synaptic) to install the package.

I believe the next version of Ubuntu (Edgy Eft) may be implementing something called Smart Package Manager.

---

### Post by Henrythewound on 2006-07-05
Aysiu, I believe you are one of the people I was referring to when I mentioned people told me to use aptitude instead of the synaptic package manager. I see your points, and I definitely like the no hassle (and complete) removal of something I wanted to try out and didn't end up liking.

As a newbie, I like the GUI of the package manager, but I never know which files I do/do not need to run a new program (I guess these are called dependencies?), so aptitude takes the guesswork out of it for me. Thanks for the replies

-J

---

### Post by aysiu on 2006-07-05
Well, Synaptic will *install* the dependencies for you automatically--it just won't *remove* those dependencies later.

A stop-gap measure in the meantime is to use *gtkorphan* to isolate "orphaned" packages that used to be dependencies but no longer have packages depending on them.

---

### Post by Jucato on 2006-07-05
Normally, Aptitude would be better when installing packages that have numerous dependencies, like ubuntu/kubuntu/xubuntu-desktop, kde/kde-core/kdebase packages, etc. For single or just a dozen packages, you could still use Synaptic. What's nice about Synaptic is that it keeps a history of what was installed/removed/upgrade and when it happened. 

There's also a way to make Synaptic sort of handle metapackages. It's not the same as aptitude. It's more of a workaround using a less known Synaptic feature.

[http://www.ubuntuforums.org/showthread.php?t=141409]("http://www.ubuntuforums.org/showthread.php?t=141409")

EDIT: AFAIK, the difference between remove and purge is that remove just uninstalls the package while purge uninstalls the program and removes its configuration files. aptitude purge is identical to apt-get remove --purge. One thing about Aptitude purgine metapackages, it only purges the metapackage, but not the dependencies. for example *sudo aptitude purge xubuntu-desktop* will remove/purge xubuntu-desktop, but will only remove (no purge) the stuff installed with xubuntu-desktop.

---

### Post by aysiu on 2006-07-05
[QUOTE=Fenyx]Normally, Aptitude would be better when installing packages that have numerous dependencies, like ubuntu/kubuntu/xubuntu-desktop, kde/kde-core/kdebase packages, etc. For single or just a dozen packages, you could still use Synaptic. What's nice about Synaptic is that it keeps a history of what was installed/removed/upgrade and when it happened. 

There's also a way to make Synaptic sort of handle metapackages. It's not the same as aptitude. It's more of a workaround using a less known Synaptic feature.

[http://www.ubuntuforums.org/showthread.php?t=141409](http://www.ubuntuforums.org/showthread.php?t=141409)[/QUOTE]
That is cool, Fenyx. Thanks for sharing that Synaptic HowTo.

Personally, I don't care. I use *aptitude* because I like it, but I'm not one of those neat-freaks who has to clean out every stray *lib* in the system. If I have orphaned packages, I certainly have the hard drive space to house them (and clothe them, too).

As it stands now, my entire installation is about 3.5 GB, which includes all my extra programs, three major desktop environments, and my home folder settings (excluding files, music, pictures, etc.).

---

### Post by Jucato on 2006-07-05
[quote=aysiu]That is cool, Fenyx. Thanks for sharing that Synaptic HowTo.

...

As it stands now, my entire installation is about 3.5 GB, which includes all my extra programs, three major desktop environments, and my home folder settings (excluding files, music, pictures, etc.).[/quote]

You're welcome. I made that HowTo for those who might prefer to use the GUI, but still want some sort of "smart" dependency handling. But it's not a real solution, though.

We both have the same installation size. Mine is also 3.5GB, with extra programs (inkscape, KOffice suite,blender, some utilities), the 3 major desktops, too (ubuntu,kubuntu,xubuntu). Only difference is my home folder is on a different partition, and currently occupies more than 5GB, mostly because of Linux ISOs I'm downloadng. :D

---

### Post by aysiu on 2006-07-05
It's not as different as you might think. Instead of a separate /home partition, I have a separate documents partition, whose folders I symlink to my /home folder.

---

### Post by Jucato on 2006-07-05
Oh that's nice. Then we are similar, again, in another aspect. My /home directory is on a separate partition from the / directory, but my Music directory is also on another partition, symlinked to my /home directory. :D

Going back to the topic, do you know of anyway to make the purge option in aptitude apply to all the dependencies of a metapackage? For example, if (but most likely not :D) I want to remove xubuntu-desktop, is there a way that all the stuff installed with it will also be purged, not just the xubuntu-destkop metapackage?

---

### Post by aysiu on 2006-07-05
I'm not sure exactly what the purge option is, to be honest.

---

### Post by vali on 2006-07-05
Am I the only one that still uses dselect? :confused: :D :D

---

### Post by Sef on 2006-07-18
> 'm not sure exactly what the purge option is, to be honest.

Purge deletes the package including any configuration files.

---

