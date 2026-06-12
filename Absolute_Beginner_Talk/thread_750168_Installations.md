---
title: "Installations"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by NikS on 2008-04-09
Y dont the packages in Linux and Ubuntu include all their dependancies within them??
It'll be a LOT MORE easy to install them!! Just like windows: a simple double-click.
Since i have shifted from windows to ubuntu and i do not have an internet connection on my home computer it becomes very difficult, then have to try many other things like nonetdebs etc etc.. & m sure there'l be many like me!!

From what i learnt it does not harm reinstalling a dependency, then y arent they included with the every software that needs it????

---

### Post by ibutho on 2008-04-09
I understand your frustration and back in the day when I started using Linux, I tought the same thing until I learnt about the extensive use of shared libraries in Unix and Unix like OSes. If each package included all its dependencies, then installations would be pretty large and you could end up with many package conflicts. For example, GNOME depends on Xorg and so does KDE. Imagine if KDE and GNOME shipped their own versions of X. It would be a recipe for disaster. Shared libraries make it easier for applications to share the same libs without including them as part of the package. Some packages (usually third party) come statically compiled so include all required deps, but I've only ever seen a few of these.

---

### Post by miesnerd on 2008-04-09
coming from windows, i understand what you're thinking. What you need to understand is that the linux way is truly better. It might seem like quite the frustration that its not done "the windows way" but once you've used linux for a while, I suspect you'll be happy that its not done "the windows way".

here's why:
linux's modular approach to OS's, libraries, and packages mean a few things:
a) easier to update
b)easier to install programs -- ie - i can sudo apt-get install whatever I want together and my linux system doesnt mind, more or less

also, linux (and of course, unix) have never worked that way. Unix is way before windows' s time, and it was built on a system connected to and (at one point) exclusively using the internet. 
Ubuntu has come up with a relatively creative way of being able to put packages on a cd, download them, and install them.

Also, if you're frustrated about this, I suggest giving different flavors of linux a try. Afterall, there are only hundreds to choose from. While I love ubuntu, the first that come to mind are things like Sabayon (where it comes with 4.7 GB of software) so you're usually not having to install anything extra or something like Nimblex, where you can  choose what you want installed, and it creates an .iso just for you.

Miesnerd

---

### Post by Tomatz on 2008-04-09
Take your computer to somewhere with an internet connection and use this:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

It will allow you to put the whole of the ubuntu repositorys onto cd's ;)

---

### Post by ramjet_1953 on 2008-04-09
It's all a matter of learning to crawl, before you walk.

If you enable the additional repositories in Applications>Add/Remove , by clicking on the Show box in the top right hand corner, you will have a very large choice of applications that are painlessly installed.

After you are comfortable with this, migrate to the Synaptic Package Manger and learn how to add even more more repositories and keys.

Too many people try to compile programs, before they understand what they are doing and fall into the dependency trap.

Remember Linux is not Windows, so no matter how Windows savvy you may be, you still have a lot of learning to do.

Most Windows users have taken years to learn how to drive it, so be patient and enjoy the learning experience that you will have with Linux.

Regards,
Roger 8)

p.s. I agree with other comments that having a central repository for libraries is vastly superior than Windows DLL system and multiple copies with each program installed.

---

