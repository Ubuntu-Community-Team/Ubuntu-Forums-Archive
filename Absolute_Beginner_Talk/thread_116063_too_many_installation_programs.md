---
title: "too many installation programs"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by wwuster on 2006-01-11
I only installed ubuntu today. I know very little about it. The initial installation went ok. Then I start trying to install some extra things and I am finding that the things I need are not listed in the "official" pkg manager (synaptic):

nvidia driver (at least listed as such)
anjuta
gvim

I'm told that I have to use apt-get or automatix, and/or enable 'hidden' repositories in synaptic. So far, I think that this is the biggest flaw of ubuntu. There should be ONE package manager that just works. I have no idea how many other installer programs there are for ubuntu and which one you must use to install a particular application, but it is very frustrating to know how to install things.

William

---

### Post by Turtle.net on 2006-01-11
In fact there is only one package manager : synaptic.
The "apt-get" instruction is in fact the instruction existing behind synapti*c.
automatix is only a script allowing you to easily install all the packages you need.
Extra repositories are important to install to have a lot of software available in synaptic.
You can have a look to [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Good luck there is light at the end of the tunnel ;)

---

### Post by gitfiddler on 2006-01-11
There are actually several ways to install programs, synaptic is probably the easiest. As your proficiency with Linux grows, you may want to try different methods, or install programs that are not available in the usual repositories.  It's nice to know that you have options available!

---

### Post by gregwa on 2006-01-11
You might also check out the unofficial Ubuntu Starter guide at [http://ubuntuguide.org/]("http://ubuntuguide.org/").

When ever possible, use Synaptic.  It is safe, makes sure dependencies are all met and gives a history of what installs/uninstalls have been done.

That being said, you should also get comfortable with the apt-get side of things.  Sometimes it's the only way to go.  98% of the time Synaptic works well.  However, if something breaks bad, apt-get will get you out of most problems.

Hope this helps,

Greg :D

---

### Post by benplaut on 2006-01-12
The reason things like Nvidia drivers, multimedia codecs (to play mp3, etc), java, and flash can't be included is because of legal restrictions.

The extra repositories are disables by default both because of legalities (Multiverse repository), or becuase when you buy Ubuntu support from Canonical, they only support packages in the default enabled repositories - 17000 is alot of packages to provide support for.

---

### Post by Deaf_Head on 2006-01-12
[QUOTE=wwuster]I only installed ubuntu today. I know very little about it. The initial installation went ok. Then I start trying to install some extra things and I am finding that the things I need are not listed in the "official" pkg manager (synaptic):

nvidia driver (at least listed as such)
anjuta
gvim

I'm told that I have to use apt-get or automatix, and/or enable 'hidden' repositories in synaptic. So far, I think that this is the biggest flaw of ubuntu. There should be ONE package manager that just works. I have no idea how many other installer programs there are for ubuntu and which one you must use to install a particular application, but it is very frustrating to know how to install things.

William[/QUOTE]

there is only one installation program, it's called the synaptics package manager.
apt-get is just a way to use the repositories synaptics uses witout opening up synaptics.

automax isn't an installer, it's a way to be lazy and to get alot of the things done without more than a few clicks.

as far as 'hidden repositories' ... they aren't hidden .. tey jsut aren't supported by ubuntu and often contain tings that may or may not be illegal depending on your location. (such as the ability to play certain types of media files such as mp3's)

Just stick with it for a few days, once you udnerstand what is going on everything becomes very natural.

---

### Post by wwuster on 2006-01-12
Once I found out how to show the 'hidden' apps in synaptic I found the things I was looking for and all is up to date now. One set of instructions that I read said to cause those to appear by some other method which I couldn't get to work. 

Is synaptic just a graphical interface to apt?

William

---

### Post by mostwanted on 2006-01-12
[QUOTE=Deaf_Head]there is only one installation program, it's called the synaptics package manager.
apt-get is just a way to use the repositories synaptics uses witout opening up synaptics.[/QUOTE]

It's the other way around. Apt-get is the package manager, Synaptic, Adept, Kynaptic and so one, are all GUI applications that use apt-get underneath.

---

