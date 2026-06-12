---
title: "Packages vs double click to install.... lil help"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-06-19
I know that ubuntu uses the package manager and repositories to install programs, but I still get hung up on my windows habits. I'm used to going to a website, downloading a file for a program I want, and double clicking on it and watching it install.  Is this sort of thing completely done away with in ubuntu? Do you never download files outside of repositories and install them from your desktop? Last time I tried to download a file for a program, it was a file I didn't know what to do with as it didn't automatically execute or anything.

The repositories seem great, but I guess I'm confused about how I'd work without them.

---

### Post by p_quarles on 2007-06-19
There are ways to install without using the repos, but it's not a good idea, especially if you're new to Linux. Installing downloaded packages can have negative consequences sometimes, and synaptic is really a lot easier to work with. 

But, since you asked, here's the basics: if you find a Debian package (ends with .deb), you can download it, then install it by typing ```
sudo dpkg -i {name of package}
```

Really, though, using the package manager is better.

---

### Post by newlinux on 2007-06-19
There are still some .deb files that you basically download and double click on and install with Gdebi, but they have the be the right .deb for your distro and release. And of course there are tarballs that sometimes behave that way, with the exception that you may  have to run a script to compile and/or install.

---

### Post by moredhel on 2007-06-19
Also, the advantage with repos is that everything is in one place, so you don't have to go round websites downloading software and then keeping them up to date, as you have the update manager ;)

There's something window's could do with :P

---

### Post by p_quarles on 2007-06-19
> **moredhel said:**
> Also, the advantage with repos is that everything is in one place, so you don't have to go round websites downloading software and then keeping them up to date, as you have the update manager ;)

There's something window's could do with :P
Very true. With synaptic, especially, dependencies are automatically found for you. If you get a .deb without everything it needs, you can spend a lot of time tracking things down.

---

### Post by defrex on 2007-06-19
Here is a complete guide:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

But the short of it is this: it's always better to use the repos when possible. If the software you want isn't there, or you want a newer version, you can get a download from the site like you would with Windows.

To do the kind of easy click-to-install installation, you need a .deb file. Those should install very easily, like you would expect form a windows installer.

In the case that you can't find a .deb, you need to compile. Traditionally, you extract the (probably tar) archive you downloaded, and cd (cd /directory/of/app/app-name.version/) to the directory in a terminal. Then:
```
./configure
make
make install
```

That's the standard, anyway. Often there'll be a readme file in the archive telling you how to compile if it's any different.

---

### Post by -Ghost9- on 2007-06-19
Thanks all!  I know it's better to use repos, but I want to be able to install without them if I need to and I just wasn't getting what I was supposed to do. Thanks for the very helpful posts and links!

---

### Post by BarfBag on 2007-06-19
It's recommended to install stuff from the repositories (better supported), but if a package is not in them or if you want the latest version, you have two options.  One - you could compile the package.  This is kinda complicated and takes long periods of time, so I don't recommend doing it unless it's absolutely necessary.  Two - you could download the .deb file and install it.  This is the easiest option.  In Feisty Fawn, all you have to do is double click on the .deb (which is the way you said you prefer it) and it will install.  It even takes care of dependencies.  This brings up the question - where do you get the .deb's?  A great site that has a lot of them is [GetDeb.net]("http://www.getdeb.net/").  Hope this helps.

---

### Post by Rui Pais on 2007-06-19
This seems to boils down everything anyone needs to know about install stuff on Ubuntu... and with pics!

hth

---

### Post by vexorian on 2007-06-19
Hi, if you download .deb packages most of the times a double click on them and install is possible, unless you don't have the correct dependencies.

---

### Post by -Ghost9- on 2007-06-19
for us windows converts, i think it'd be cool if on website for programs, like messengers or something, it somehow could link you to a repository if that program is already in one. I'm so used to reading about programs on websites and then downloading them that I stutter when trying to figure out how to get from reading about the program to actually using it. I know for the most part it's a very simple search through the repositories, but it's just a thought to make a shortcut for us slow learners.

---

### Post by Rui Pais on 2007-06-19
> **-Ghost9- said:**
> for us windows converts, i think it'd be cool if on website for programs, like messengers or something, it somehow could link you to a repository if that program is already in one. I'm so used to reading about programs on websites and then downloading them that I stutter when trying to figure out how to get from reading about the program to actually using it. I know for the most part it's a very simple search through the repositories, but it's just a thought to make a shortcut for us slow learners.

Simple:
go here:
[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)
Non official debs;
[http://www.getdeb.net/](http://www.getdeb.net/)

You can even download the deb you want and clic on it installing using gdebi... is like Windows ;)

---

### Post by -Ghost9- on 2007-06-19
> **Rui Pais said:**
> Simple:
go here:
[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)
Non official debs;
[http://www.getdeb.net/](http://www.getdeb.net/)

You can even download the deb you want and clic on it installing using gdebi... is like Windows ;)

Hey that's awesome! but not really what I meant. That's a collection of everything. I'm talking more about a single promotional site for a program. For instance, open office. It's easy to get from a repository i know, but when I first heard about it I went and looked at their website. They have a bunch of download links for the different platforms which I think is great! But I just thought it would be cool, since that program is in a repository, that either instead of or along with, there could be a link or something that when you clicked on it triggered the package manager to find Open Office in the repos. just a thought...

---

### Post by p_quarles on 2007-06-19
That just wouldn't work, because the repositories are all specific to certain distros of Linux, but the programs themselves will (generally speaking) run on all Linux and most Unix systems. The reason it works that way for Windows is because it's a monolithic operating system. Linux isn't. 

That said, many of the project sites you do visit list the repositories in which the program is available for a few of the more popular distros.

---

### Post by bobplano on 2007-06-19
> **p_quarles said:**
> That just wouldn't work, because the repositories are all specific to certain distros of Linux, but the programs themselves will (generally speaking) run on all Linux and most Unix systems. The reason it works that way for Windows is because it's a monolithic operating system. Linux isn't. 

That said, many of the project sites you do visit list the repositories in which the program is available for a few of the more popular distros.

for instance wine has you add their repo instead of just linking to the deb, so you can go visit their site to see what its about, but still get the advantage of downloading from the repos

---

