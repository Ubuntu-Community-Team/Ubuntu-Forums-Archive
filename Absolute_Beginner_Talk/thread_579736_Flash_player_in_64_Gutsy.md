---
title: "Flash player in 64 Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by eljaydub on 2007-10-18
I'm going to make the switch to Gutsy pretty soon but I'm wondering about the flash player issues in 64bit Gutsy. Is it still a pain? Or has something been implemented to take care of that for you?  I'm running 64bit Fiesty and never did get my flash player to work... If it's still an issue maybe I'll just install 32bit Gutsy? 
Cheers

---

### Post by Paul820 on 2007-10-18
You can get flashplayer from the repos now. Just > sudo apt-get install flashplugin-nonfree from the terminal.
I use 64bit gutsy and it works fine.

---

### Post by FredB on 2007-10-18
> **Paul820 said:**
> You can get flashplayer from the repos now. Just  from the terminal.
I use 64bit gutsy and it works fine.

You're right. It is the best until Gnash become really useful.

---

### Post by heon2574 on 2007-10-19
> **Paul820 said:**
> You can get flashplayer from the repos now. Just  from the terminal.
I use 64bit gutsy and it works fine.

```
sudo apt-get install flashplugin-nonfree
[sudo] password for htk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

```

It doesn't work :(

---

### Post by 001100 on 2007-10-19
servers might be buzy

---

### Post by FredB on 2007-10-19
> **001100 said:**
> servers might be buzy

Not might. They're over used right now. Getting a light package as xinetd (28 Kb) took around 5 minutes a few hours ago :(

---

### Post by Jasongates on 2007-10-19
I believe you need to enable the repository "Software restricted by copyright or legal issues" in Applications -> Add/Remove and then click on Preferences And select the repositories. Just check them all to be safe, thats what I did and it worked fine after.

---

### Post by Martin123 on 2007-10-22
I can't install the Flash player in 64 Gutsy.

Code:

> martin@martin-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by Seisen on 2007-10-22
You guys need to enable the multiverse repository in order to install Flash.

---

### Post by Maestro23 on 2007-10-22
> **Martin123 said:**
> I can't install the Flash player in 64 Gutsy.

Code:

Make sure you have Universe and Multiverse repos enabled.

System>> Admin>> Software Sources.

---

### Post by lamnk on 2007-10-25
Did the command, flash plugin was installed but nothing happens. Reboot and it's still the same.

---

### Post by lamnk on 2007-10-25
Sorry double post

---

### Post by bone2006 on 2007-10-26
I think that package isn't available in the 64 repository. I tried the samething as posted and it's not available.  All the repositories are enabled and I think the people making comments are the ones running 32bit ubuntu as I'm getting the samething as other people are

sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package flashplugin-nonfree has no installation candidate

is only available from another source
E: Package flashplugin-nonfree has no installation candidate

---

### Post by panki on 2008-03-10
Maybe installing ia32-libs?  This would enable the 32 bit libraries

---

