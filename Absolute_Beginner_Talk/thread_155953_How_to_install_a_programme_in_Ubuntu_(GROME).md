---
title: "How to install a programme in Ubuntu (GROME)"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by nmcuong on 2006-04-06
Hi everybody, I am quite a new user of Linux. I do not know basics of UNIX either. Recently I downloaded and install Ubuntu 5.10 on my machine and started to learn how to use Linux. But, I have problems with installing Skype and some other additional programs. I have downloaded *.deb files but I do not know how to run the installation. Can anybody help me with that? Many thanks

---

### Post by meborc on 2006-04-06
to install a *.deb files use a command in terminal:
**dpkg -i <filename>.deb**
sometimes you have to use
**sudo dpkg -i <filename>.deb**
to understand why sudo is sometimes needed read: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

and for further help on installing stuff, read the breezy guide in my sig!

the best way to install programs in ubuntu is via synaptic (in the system menu), read more - [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by Edward The Bonobo on 2006-04-06
When I started using Ubuntu very recently, I found it very difficult.  It's not the same as Windows.  You don't (usually) just download a programme and click on it to install.  There are some concepts which is helpful to understand.

In fact, Ubuntu is very clever.  Most of the applications you need are stored on the web in the 'Ubuntu Repositories.'  There are different ways you can tell Ubuntu to go and get an application: [LIST]
[*]Using the Terminal window, you can run an application called 'apt-get'
[*]There's a graphical installer called 'Synaptic'
[*]In Gnome, there's also an automatic Update Notifier which lets you know when there's a new version of something you've already got and downloads it for you.
[/LIST]
One of the reasons why this is all so good is that Linux is very modular: a Package (as programmes are called in Linux) may depend on other packages.  The download method automatically keeps track of all these dependencies and downloads all the sub-modules you need.

There are different categories of Ubuntu packages.  These are kept in different repositories.  In the default Ubuntu, you are given the main repositories.  But you can also configure it to look at some additional repositories ('Universe' and 'Multiverse').  This can be done easily, either via Synaptic or by editing a text file (/etc/apt/sources.list).  You can also non-Ubuntu add repositories - but this can cause problems.  Also, some of them require you to have a GPG key.

You can also install software from a .deb file.  You have to open a terminal and type: 
```

sudo dpkg -i *filename.deb*

```

Or...sometimes you might have a .rpm file (from another flavour of Unix).  You convert this to a .deb by typing:

```

sudo alien *filename.deb*

```

There's some good documentation available...but I found that I didn't know where to look until I'd understood the concepts I've just described.  It's a good idea to look at the Starter Guide:
[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

And here's something about adding repositories using Synaptic.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

That's a lot of information - possibly you know some of this already.  I've tried to capture the things I didn't know when I started and put them in one place.

Welcome to the strange and frightening world of Ubuntu.  Have fun!

---

### Post by Edward The Bonobo on 2006-04-06
Nearly forgot:

There's one more way of installing packages and configuring things which aren't in the default Ubuntu (some of them for licensing reasons)...a gizmo called Automatix which automates some downloads of common tweaks and additions:
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by nmcuong on 2006-04-07
Thank you very much. That helps a lot. I will try as guided.

---

