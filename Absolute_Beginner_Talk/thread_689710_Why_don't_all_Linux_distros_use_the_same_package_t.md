---
title: "Why don't all Linux distros use the same package types?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-02-06
What is the difference between .rpm and .deb for example? Why would one set of developers prefer one over the other?


Since all Linux distros use the same kernel, doesn't Firefox on Red Hat do exactly the same thing as Firefox on Debian, regardless of whether it started life as a .rpm or .deb?

In that case, why can't a distro use an app to install .debs and a different app to install .rpms? I heard the it has something to do with how dependencies are handled; can someone explain that more precisely for me?

---

### Post by steveneddy on 2008-02-06
It's just a packaging system.

.deb is for a debian based distro because they usually use Synaptic or apt.

.rpm is for yum based packaging.

It keeps some people from using the Red Hat .rpms for some of their proprietary file software.

---

### Post by Tyke91 on 2008-02-06
rpm (I think it stands for RedHat Package Manager... it may be wrong tho) was developed by the red hat company. It was built to compile on red hat (or fedora, or any derivative there-of of redhat). The company use it to access their servers and download dependencies from their own updated files.

deb was created by the people who wrote debian. It is built to compile on Debian systems (Pclinux OS, knoppix, Ubuntu, etc) and it uses the apt system to install dependencies.

alternately you can download a tar.gz file and compile your own package from source (and find all dependencies your self) but alot of us are too lazy to do that.


I may be wrong in some explanations, so feel free to correct me any time :)

---

### Post by jordanmthomas on 2008-02-06
The reason there's different types of packaging is that the people who create the different systems have different ideas as to how package management should work.  

Competition is a good thing, really.  Would you rather be forced to use only debs?  (I know a lot of people here at the Ubuntu forums would scream YES, but you surely see what I'm saying.)

You ask why distros can't use both rpms and debs.  Well, they can in a sense.  rpm packages can be converted to debs using a program called alien, but often dependencies don't work very well this way.

Technically, the difference is that rpms are based on using cpio and debs use ar.

---

### Post by jordanmthomas on 2008-02-06
> **steveneddy said:**
> .deb is for a debian based distro because they usually use Synaptic or apt.

.rpm is for yum based packaging.

You can use apt with rpms :)
The package managers are built around the packages they handle, not the other way around.  So rpm isn't "for yum".

---

### Post by jaytek13 on 2008-02-06
People seem to be mentioning package managers... .deb and .rpm packages existed long, long before apt and yum ever came into existence.

So, that's actually a good question from the OP that I've never really thought of. What is happening in the background or what is the defining difference as to why you need to use a rpm package with a rpm system and a deb package with a deb system? Hmmm.

---

### Post by jordanmthomas on 2008-02-06
> **EmosSuck777 said:**
> 
In that case, why can't a distro use an app to install .debs and a different app to install .rpms? 

Sorry to make so many posts here, but I just read this about smart

From their page:
> Using multiple package managers at the same time (like rpm and dpkg) is possible, even though not the software goal at this moment. 

And of course there's alien, like I mentioned earlier.

---

### Post by NeoGreen on 2008-02-06
I was always under the impression that apt and yum where command used to retrieve programs.....of course depeding on the distro that you have be a redhat based or debian based.

---

