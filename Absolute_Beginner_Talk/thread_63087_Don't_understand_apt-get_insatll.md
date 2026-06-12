---
title: "Don't understand apt-get insatll"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by ronlondre on 2005-09-06
Hi,
I'm having trouble with the apt-get install command. For example; as listed in the starter guide I downloaded gDesklets, then opened the terminal, typed: sudo apt-get install gdesklets.   Tthe following is what i typed and the message i received:
ronlondre@ubuntu:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets

What's happening? This happens regardless of the application I download and try to install.
HELP

---

### Post by Kapre on 2005-09-06
[QUOTE=ronlondre]Hi,
I'm having trouble with the apt-get install command. For example; as listed in the starter guide I downloaded gDesklets, then opened the terminal, typed: sudo apt-get install gdesklets.   Tthe following is what i typed and the message i received:
ronlondre@ubuntu:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets

What's happening? This happens regardless of the application I download and try to install.
HELP[/QUOTE]

ronlondre - did you changed/update your sources.list? If not, please use [this](http://www.ubuntuguide.org/#repositories) . I just installed gdesklets last night.

K

---

### Post by ronlondre on 2005-09-06
I can't seem to get the gedit command to work. I am using KUBUNTU. This might have something to do with it.
Here are my results when using the gedit command:

ronlondre@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
ronlondre@ubuntu:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found

Any advise?

---

### Post by aysiu on 2005-09-06
gedit is a Gnome application. I think in Kubuntu (which uses KDE, not Gnome), the command is kedit.

apt-get looks at some repositories (where applications are stored) and downloads and installs them for you. If you enable extra repositories

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

you have more applications to choose from. You may need to do that in order to get gdesklets. I'm not sure if gdesklets work in KDE, though.

There's also a graphical front-end for apt-get called Synaptic Package Manager:

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

By the way, I love the Ubuntu Guide, but it is a bit Gnome-centric (since Ubuntu defaults to Gnome). Check out the Kubuntu guide for more KDE stuff:

[http://kudos.berlios.de/kf/kf1.html](http://kudos.berlios.de/kf/kf1.html)

---

### Post by Wolki on 2005-09-06
[QUOTE=aysiu]you have more applications to choose from. You may need to do that in order to get gdesklets. I'm not sure if gdesklets work in KDE, though.[/QUOTE]

I guess they could work...  think the KDE equivalent is called SuperKaramba.

so "sudo apt-get install superkaramba" should do the trick.

as for editors, there are several in kde. kedit, kate and i think kwrite. i don't know why there are so many, i guess the kde teeam likes editors :)

---

