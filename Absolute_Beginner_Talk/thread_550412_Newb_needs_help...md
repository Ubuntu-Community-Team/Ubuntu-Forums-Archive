---
title: "Newb needs help.."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by CSI800 on 2007-09-13
I cant seem to access my root directory in the terminal..I enter my password and it says not valid. My password works for log in and other admin tasks./   The reason I ask is that I am having trouble installing anything that I download.  I downloaded a program called katapult but ofcourse cannot open it..Any help would be great.

Thanxs Csi guy

---

### Post by felicity on 2007-09-13
There is no user-set root password in ubuntu by default. The password you're entering is your user password. Ubuntu is setup to where sudo uses the user password, hence causing some confusion for people used to using the root password on sudo and also on the root account.

What do you mean you "cannot open" a program you downloaded? Are you saying you're trying to install it? Is it a .deb file?

---

### Post by Maestro23 on 2007-09-13
RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

Hope you are not trying to compile something from source.  Can be a major headache for someone new to linux.

If the file you d/l is a tar.gz or .tar.bz2, you will need to take a look at the following section in the Feisty Starter's Guide:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Working_with_archives_and_packages](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Working_with_archives_and_packages)

Also the section below it, [COLOR="Red"]Compiling from Source[/COLOR].

---

### Post by CSI800 on 2007-09-13
I am trying to install software, I am such a newb I barely know how to explain what I cant do..lol
It says in the readme to use the terminal and find the directory using CD.. I dont know how to do this

thanxs  :)

---

### Post by Maestro23 on 2007-09-13
> **CSI800 said:**
> I am trying to install software, I am such a newb I barely know how to explain what I cant do..lol
It says in the readme to use the terminal and find the directory using CD.. I dont know how to do this

thanxs  :)

Make things easy on your self.  Katapult is in the Repos.  Two ways to get:

> Synaptic (GUI): Open up Synaptic and search for "katapult". Mark for installation.
or
Terminal (type):

sudo apt-get install katapult


Also some links you might want to take a look at:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

*Link to the Feisty Starter's Guide in my sig.

Welcome to Ubuntu man. :guitar:

---

### Post by CSI800 on 2007-09-13
Thanxs a bunch that command line worked perfectly...Cheers M8

Csiguy

---

### Post by asmoore82 on 2007-09-13
if you are running Ubuntu 7.04, **katapult** is in the *Repos*(Repositories)
and you can have it installed automagically by searching for it in Synaptic
in Gnome, open "System -> Administration -> Synaptic Package Manager"
In KDE, you would have to use "Adept" I think.

you could install it in a terminal with the commands
```
~$ sudo apt-get update
~$ sudo apt-get install katapult
```

EDIT: it is late, *or is it just **ME!*** :lol:

---

### Post by Maestro23 on 2007-09-13
> **CSI800 said:**
> Thanxs a bunch that command line worked perfectly...Cheers M8

Csiguy

No prob man.:)

---

