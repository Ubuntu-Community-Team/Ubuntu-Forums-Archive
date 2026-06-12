---
title: "What have I got myself into NO GUI"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by nowatkins on 2007-05-08
WOOAAAHHHH! Look at this learning curve. I'm new to the Linux world. I need to find a command list and their functions. If anybody can help please do!!

---

### Post by Vorian on 2007-05-08
I'm going to plug a couple of sites.

[http://www.psychocats.net/](http://www.psychocats.net/) which is aysiu's site.  It is a great spot for beginners.
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/) great stuff

and more....

I'm sure some other folks will jump in here too!

Welcome to Ubuntu!

---

### Post by Iceni on 2007-05-08
I'm just going with welcome :)

These forums are your best friend, belive me!

---

### Post by crimesaucer on 2007-05-08
These are my favorite three that help me understand some things:

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

and the ubuntu wiki pages help too...
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

and the desktop manual:
[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

---

### Post by Blondie on 2007-05-08
Yep, describe accurately and completely any problems you have and these forums will probably blow you socks off with the speed and usefulness of the replies, particularly for simple newbie stuff.

---

### Post by milton1 on 2007-05-08
Simple, straight forward:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by Tomosaur on 2007-05-08
> **nowatkins said:**
> WOOAAAHHHH! Look at this learning curve. I'm new to the Linux world. I need to find a command list and their functions. If anybody can help please do!!

Uhh, just in case you're wondering - you're supposed to have a GUI. If you don't have one, chances are you downloaded the server edition, or, if not, then something is broken.

---

### Post by nowatkins on 2007-05-08
Yeah, I wanted to install the server edition. I also saw on other post on how to get the gui install on top. I having trouble with it, but I will search the forums first. I know its here somewhere. Thanks for your help. One day I will be the helper instead of the helpee.

---

### Post by nowatkins on 2007-05-08
What is the difference between the server and desktop editions. I see in other post the only thing is the gui. Is that correct?

---

### Post by bobplano on 2007-05-08
the server edition installs less software as a server doesn't need so many things plus the fact that there is no GUI. to install a GUI just do 
sudo aptitude install (x)(k)ubuntu-desktop
that will also install the programs associated with those desktops so you don't have to install so many programs yourself

---

### Post by Spinelli on 2007-05-08
> **nowatkins said:**
> What is the difference between the server and desktop editions. I see in other post the only thing is the gui. Is that correct?

The server edition comes with no GUI and very few applications installed by default. It is intended to be used as a server. You could install apache, sendmail, openssh, cups, samba, or whatever you want. I run the server edition as a NFS server on my local network and it works great. The desktop edition has a graphical installer and comes with GNOME and other graphical desktop productivity applications already installed like OpenOffice, Firefox, Evolution email client, and Rhythmbox music player. 

If you are running the server edition and want to install the GUI I believe you would type the following at the command line:

```

sudo apt-get install ubuntu-desktop

```
 
I have compiled at list of GNU/Linux links and posted them on my website located here.
[http://www.catgrepsort.com/gnulinux/links.html]("http://www.catgrepsort.com/gnulinux/links.html")

I hope that helps.

---

### Post by nowatkins on 2007-05-08
When I do the desktop install. I have problems with dependencies. I am a windows server administrator. This si what i have done so far.
Install server edition 6
Change the sources.list from drappy to feisty.

Could that be the problem?
Would it be possible to use the gui edition and remove most of the fluff?

---

### Post by jfinkels on 2007-05-08
> **nowatkins said:**
> When I do the desktop install. I have problems with dependencies. I am a windows server administrator. This si what i have done so far.
Install server edition 6
Change the sources.list from drappy to feisty.

Could that be the problem?
Would it be possible to use the gui edition and remove most of the fluff?

You might have some problems if you manually edited your sources.list file to change "dapper" entries to "feisty"...it's recommended to do distribution upgrades sequentially (i.e. Ubuntu 6.06 Dapper Drake -> Ubuntu 6.10 Edgy Eft -> Ubuntu 7.04 Feisty Fawn).

To install the GUI, just type the following:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Spinelli on 2007-05-09
> **nowatkins said:**
> When I do the desktop install. I have problems with dependencies. I am a windows server administrator. This si what i have done so far.
Install server edition 6
Change the sources.list from drappy to feisty.

Could that be the problem?
Would it be possible to use the gui edition and remove most of the fluff?

That is definitely the problem. In general if you have dapper installed you have to use packages from dapper. In general if you have edgy installed you have to use packages from edgy. In general if you have feisty installed you have to use packages from feisty. I think here is a way to mix and match packages from different releases, but I do now now enough about APT to fully understand it. I would recommend reading the two articles bellow. 

[https://help.ubuntu.com/community/AptGetHowto]("https://help.ubuntu.com/community/AptGetHowto")
[http://www.debian.org/doc/manuals/apt-howto/index.en.html]("http://www.debian.org/doc/manuals/apt-howto/index.en.html") 

Then read the following man pages:

```
man apt-get
```
```
man apt-cache
```
```
man apt-cdrom
```
```
man dpkg
```
```
man dselect
```
```
man sources.list
```
```
man apt.conf
```
```
man apt-config
```
```
man apt-secure
```
```
man apt_preferences
```
The APT users guide is located in /usr/share/doc/apt-doc/

NOTE: After editing /etc/apt/sources.list you must run the following command:
```
sudo apt-get update
```

That should keep you busy for a while. Have fun!

---

### Post by MS-DOS4 on 2007-05-09
I've discovered that linux users are 100% more willing to help and 100% more friendlier than windows/apple users. It's very nice and that is why I got my new linux up and running so quick.

---

### Post by ssam on 2007-05-09
it is not recommended to do an upgrade by editing to source list. there is a recommended command line upgrade method at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by nowatkins on 2007-05-09
I love this Ubu. Did a reformat and complete reinstall in less than 30 minutes. Windows can top that. I am now back at step 1.  Used sudo vi to try to change back to drapper. Could get it to write back. I still amazed at the 30 minutes. The gui update is that going to be the default screen or will I have to manually start the gui. I really hope so. I really want to use the CLI, just want to GUI handy if I need it. I have never loaded a complete OS in 30 MINUTES. :guitar: :lolflag:

---

### Post by Tomosaur on 2007-05-09
> **nowatkins said:**
> I love this Ubu. Did a reformat and complete reinstall in less than 30 minutes. Windows can top that. I am now back at step 1.  Used sudo vi to try to change back to drapper. Could get it to write back. I still amazed at the 30 minutes. The gui update is that going to be the default screen or will I have to manually start the gui. I really hope so. I really want to use the CLI, just want to GUI handy if I need it. I have never loaded a complete OS in 30 MINUTES. :guitar: :lolflag:

If you don't want all of the bulk and overhead that the GUI will give you, there are very very lightweight alternatives out there. In general, the following packages:
```

ubuntu-desktop
kubuntu-desktop
xubuntu-destop

```
you should avoid if you want to keep the maximum resources for your server. xubuntu-desktop is the most lightweight there, but will still install a lot of stuff you may not need / want.

However, you can just manually install the xserver and a lightweight window manager like fluxbox. While I can understand the desire to keep to the terminal purely - it just seems to me that if you're new to Linux in general, then having the GUI around while you familiarise yourself with how the terminal works / it's capabilities etc, is the best idea. Chances are you're going to need to read lots of documentation and stuff, and although the terminal can do all of this for you (you can even browse the web in the terminal :P), I personally find that a GUI environment keeps me more level headed, and since you can tab the GUI terminal (and thus have a number of different terminals open at once), it just seems to make more sense to me.

However, each to his own!

Oh by the way, if you find that you'd like to use a tabbing system (you may not, but I find it useful), but still don't want to use a GUI, then you can just use the virtual terminals.

To switch between virtual terminals, just hit the following key combo:
```

ctrl+alt+Fx

```

where Fx is one of the F buttons up to F7. If you were using a GUI, then F7 would be the GUI, and F1-F6 are virtual terminals.

---

