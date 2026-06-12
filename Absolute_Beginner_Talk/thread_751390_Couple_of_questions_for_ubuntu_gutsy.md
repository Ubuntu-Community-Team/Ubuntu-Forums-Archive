---
title: "Couple of questions for ubuntu gutsy"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Steve S on 2008-04-10
Ok, I tried Kubuntu and had some problems, so I decided to go with ubuntu and so far, no problems with installers, updaters and so on.

Here are some questions I do have though:

1) Is there a way to make myself the admin, or should I say, so I don't have to put a password in everytime I want to install something?

2) When I go to packages.ubuntu.com to install some programs I don't see in my add/remove and use the Gdeb installer to install them, it says something about Software channel, What is three or where is that?

Other than that, I am more pleased with Ubuntu than I was with Kubuntu, although I did like the extra available packages in the installer.

---

### Post by smurphy_it on 2008-04-10
You can make yourself a "root" user, but this represents a huge security risk.

don't know about the software channel... someone else will have to answer that....

Left side can be all available application, third part applications, etc...

---

### Post by OffAxis on 2008-04-10
To answer your questions:

1. Yes. It's HIGHLY discouraged.
All you do is edit the **/etc/sudoers** file and remove the # sign from this line
```
# %sudo ALL=NOPASSWD: ALL
```

2. ? Have you enabled all the repositories in **/etc/apt/sources.list** ?
Any kubuntu package will work on ubuntu, and it's the same repo, so I don't understand...

---

### Post by Therion on 2008-04-10
sudo exists for a reason, but do as you will.

It sounds like you are being informed that a version of the software you want to download/install exists in one of the official Repos and you're being advised that installing from the Repo is a good idea.  It's up to you if you want to use the version in the Repo (which could be newer OR older than the version you're downloading) or not however.  The message itself is just informational.

---

### Post by Steve S on 2008-04-10
I go to packages.ubuntu.com and follow the links to the miror sites, download the package then open with GDebinstaller to load it. It does not show that it is installed on my menu system, but it does show installation complete when I do it that way.

---

### Post by superzorro on 2008-04-10
I don't know if this answers your second question:

Add/remove is just a list of the most common programs of the repository, however you can also easily install all the Ubuntu packages using the "Synaptic package manager" you find it under System > Administration, there you just search for the package, right click it and apply, and you are done

---

### Post by Steve S on 2008-04-10
Now that may just answer my question right there. Thank you for all the help

---

### Post by Tatty on 2008-04-10
Read this before doing any changes to your system which may remove being prompted for a password before doing administrative changes...

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

The password is there to prevent anything from altering your system without your permission.  This largely prevents viruses and spyware from installing itself on your machine.  It also prevents anyone from intentionally altering your machine without your permission.

To put it into perspective.  Imagine someone who is running windows XP, but dosent have a firewall, anti-virus or anti-spyware.  You would think they are crazy.
To a Linux user, disabling your superuser password would sound just as crazy.


Having said all that though, It is your machine so the choice is yours. :popcorn:

---

### Post by Steve S on 2008-04-10
Yeah, I had given up on the removing the password thing for now. A little inconvenient, but the likelyhood of losing my data to a virus is worse.

Thanks for the input:popcorn:

---

### Post by stchman on 2008-04-10
> **Steve S said:**
> Ok, I tried Kubuntu and had some problems, so I decided to go with ubuntu and so far, no problems with installers, updaters and so on.

Here are some questions I do have though:

1) Is there a way to make myself the admin, or should I say, so I don't have to put a password in everytime I want to install something?

2) When I go to packages.ubuntu.com to install some programs I don't see in my add/remove and use the Gdeb installer to install them, it says something about Software channel, What is three or where is that?

Other than that, I am more pleased with Ubuntu than I was with Kubuntu, although I did like the extra available packages in the installer.

TO do what you do is a HUGE security risk.  Having to type in your admin password is a very small price to pay for having good security.

---

### Post by Tatty on 2008-04-10
> **Steve S said:**
> Yeah, I had given up on the removing the password thing for now. A little inconvenient, but the likelyhood of losing my data to a virus is worse.

Thanks for the input:popcorn:

Dont worry, it becomes second-nature very quickly ;)

---

