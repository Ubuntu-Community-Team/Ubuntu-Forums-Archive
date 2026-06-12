---
title: "apt-get hylafax?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by sangria on 2006-07-16
Hey all, i'm new to linux and am trying to get Hylafax to install. First, i don't think i understand how the apt-get process works. From what i've read, ubundu is a debian based system and according to hylafax i should be able to type:

apt-get install hylafax-server hylafax-client hylafax-doc

I tried adding sudo to the front as this takes me to the root level?

sudo apt-get install hylafax-server hylafax-client hylafax-doc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package hylafax-server

suggestions? i'm very famillar with dos if it helps to explain anything. . .

---

### Post by Ragazzo on 2006-07-16
Yes, you need to be root (use sudo) when installing new programs. But you need to add extra repositories: 
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

After that you should be able to run the command.

---

### Post by sangria on 2006-07-16
thanks for the link. i tried following the instructions for backing up my current list: 
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
which asks me for my password and then takes me back to the prompt. I then enter the next step wich says:
sudo gedit /etc/apt/sources.list
and get:
sudo: gedit: command not found


I also tried using the synaptics package manager. . . i tried loading all the extra binary sources and then searching for hylafax. . . no go. ideas?

---

### Post by jimmygoon on 2006-07-16
> **sangria said:**
> thanks for the link. i tried following the instructions for backing up my current list: 
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
which asks me for my password and then takes me back to the prompt. I then enter the next step wich says:
sudo gedit /etc/apt/sources.list
and get:
sudo: gedit: command not found


I also tried using the synaptics package manager. . . i tried loading all the extra binary sources and then searching for hylafax. . . no go. ideas?

are you running kubuntu?

---

### Post by sangria on 2006-07-16
xubuntu. . . i'm trying to keep it fairly lean, but i need the hylafax to work. i just downloaded the latest version yesterday, and i ran the updates today.

---

### Post by ovimunt on 2006-07-16
EDIT: You SHOULD NOT use Xubuntu unless you have a VERY slow system. Try installing Ubuntu or Kubuntu. You'll do yourself a BIG favour. 

In any case, try a text mode editor instead:

> sudo nano /etc/apt/sources.list

Plus, you'll be better off if you use ***aptitude*** instead of ***apt-get*** i.e.

> sudo aptitude install whatever_package

The difference is that ***aptitude*** records all the dependencies of a package and if you want to remove it at a later time it is a lot more efficient then ***apt-get***.

---

### Post by sangria on 2006-07-16
i thought the only difference was the gui manager. . . a slimmer version so it used fewer resources? will this make a difference when trying to install aps? i don't see why it should. i'll start downloading it, but wait for some more info before installing.

---

### Post by ovimunt on 2006-07-16
The difference it makes is that most of the support around here is aimed at either the Gnome or KDE GUIs and some of the commands will not work, like ***gedit*** for example, because they are GUI specific - ***gedit*** is a Gnome specific graphical text editor. 

Furthermore, you'll find it a bit more difficult to install other things as you'll have to download more stuff. A good example for this are the restricted media codecs (mp3, aac, etc...). The help provided is again GUI specific because different application come or don't come with certain packages. 

And finally, some graphical applications might just not work in Xubuntu since they are Gnome or KDE specific and to make them work you might end up downloading big chunks of the Gnome or KDE GUIs...

---

### Post by angkor on 2006-07-16
> **ovimunt said:**
> EDIT: You SHOULD NOT use Xubuntu unless you have a VERY slow system. Try installing Ubuntu or Kubuntu. You'll do yourself a BIG favour. 

:confused:  You make it sound dangerous to install xfce. 

There is absolutely no reason one shouldn't install xubuntu. On a fast system xfce is faster than both kde or gnome and maybe some people prefer the xfce desktop to the others.

---

### Post by sangria on 2006-07-16
can anyone running ubuntu or kubuntu verify the existence of hylafax in those repositories? i'll be happy to switch. i'll just take a little work.

---

### Post by musper on 2007-04-20
Xubuntu-6.02

I can confirm that i did managed to get te appropriate repositories checked in the synaptic. I think you're missing Ubuntu backports repository. I did checked every other binary repository, and successfully installed hylafax-server, client and docs. While installing I had to open terminal in synaptic installation window, and go through configuration of postfix. After that i saw lot's of fallback to ? due to missing libgnome* so i assume that was client portion of hylafax and it's gnome gui. Will report further.

---

