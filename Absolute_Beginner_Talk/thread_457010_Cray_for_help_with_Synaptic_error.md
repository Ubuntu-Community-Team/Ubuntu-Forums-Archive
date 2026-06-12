---
title: "Cray for help with Synaptic error"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-28
I have just tried to run synaptic and I get this error

E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Does any one have any ideas what should do? The update manager and add/remove are giving me similar errors

---

### Post by starcraft.man on 2007-05-28
Well, since automatix is right there in the middle of the error, you were trying to install that/did install it I assume (I don't think it could be there otherwise)? Automatix2 isn't something I think should be supported here (I've stated my reasons elsewhere in discussion with other members), its not an official means of installing in Ubuntu and has caused breakage as you see. I kindly (I am not mad nor do I think ill of you for using it) direct you to [automatix forums]("http://www.getautomatix.com/forum/") for fixing this problem, alternatively uninstall it, and your synaptic should work again and use [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") or [psychocats]("http://www.psychocats.net/ubuntu/index.php") for learning how to install the official way. 

I don't want to appear rude, but they broke it they can fix it. Link to their [main site]("http://www.getautomatix.com/") for you.

---

### Post by tabithaboof on 2007-05-28
To be honest, I use automatix once to install skype and havent touched it since, this was weeks ago. The error occured when I tried to follow this guide to get access to the the ubuntu studio repo to download the theme.

[http://ubuntustudio.com/downloads](http://ubuntustudio.com/downloads)

---

### Post by guice on 2007-05-28
Remove this file: /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages

And then redo the update.

---

### Post by pluto1209 on 2007-05-28
Warning...this is my first post and advice on Ubuntu!!! Just started to use it a couple of weeks ago.

Anyway, I had the same issue..this morning I noticed there was updates pending indicates by the symbol, but then I clicked it to update, and I got the same error as above..to temporary fix it, I did this:

 sudo gedit /etc/apt/sources.list

then in my list towards the end I got
#AUTOMATIX REPOS START
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

so, inserted # for every line, and then saved the file that fixed it and I could get my updates...

---

### Post by tabithaboof on 2007-05-28
Thaks all for the advice! I actually sorted it out a different way. For some reason automatix itself was still working an option to remove the automatix repositories which I did. This fixed the problem, I then got rid of Automatix altogether via synaptec. This seemed to work ok.

---

### Post by starcraft.man on 2007-05-28
> **tabithaboof said:**
> Thaks all for the advice! I actually sorted it out a different way. For some reason automatix itself was still working an option to remove the automatix repositories which I did. This fixed the problem, I then got rid of Automatix altogether via synaptec. This seemed to work ok.

Ok then, glad to hear that (sorry for not getting back sooner, was a bit busy). For future reference, use [Ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") Very good to help installing anything. And, has a working sources list at the top with all the extra repos you might need (or should your sources list be messed up again, its a good replacement).

Have fun with Ubuntu, don't forget to put resolved in your title. :)

---

### Post by hakimaki on 2007-05-28
> **tabithaboof said:**
> I have just tried to run synaptic and I get this error

E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Does any one have any ideas what should do? The update manager and add/remove are giving me similar errors

I had the same error post the kernel upgrade.  It was fixed with a sudo apt-get update.

---

### Post by Mechanical on 2007-05-28
sudo apt-get update did fix it for me.  Furthermore, I don't see why an automatix problem cant be solved here, this is a place for anything related to ubuntu.

---

### Post by taurus on 2007-05-28
> **Mechanical said:**
> sudo apt-get update did fix it for me.  Furthermore, I don't see why an automatix problem cant be solved here, this is a place for anything related to ubuntu.

[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

### Post by arnieboy on 2007-05-28
> **tabithaboof said:**
> I have just tried to run synaptic and I get this error

E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Does any one have any ideas what should do? The update manager and add/remove are giving me similar errors

The erring package has long been fixed and a simple

```
sudo apt-get update
```

will fix this issue

---

