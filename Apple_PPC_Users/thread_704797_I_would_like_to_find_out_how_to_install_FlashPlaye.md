---
title: "I would like to find out how to install FlashPlayer on a PPC with Ubuntu"
date: 2008-02-22
forum: Apple PPC Users
---

### Post by RavenStandsAlone on 2008-02-22
I hope that is a specific enough headline to get someone's attention.

---

### Post by BladeMelbourne on 2008-02-22
You can't install the Adobe plugin on PPC Linux. Adobe releases the Linux plugin for i386, but not PPC.

If you want an open source Flash plugin, search for 'gnash' using the synaptic program. Unfortunately it doesn't work on most sites.

---

### Post by RavenStandsAlone on 2008-02-22
Okay, I have a folder saying "gnash-0.8.1" extracted to my desktop. How do I install it now?

---

### Post by bodhi.zazen on 2008-02-22
gnash is in the repos, so enable universe, 

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

then

```
sudo apt-get update && sudo apt-get install gnash
```

If you prefer a GUI, try ADD/Remove programs or synaptic.

Also ...

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

You should compile from source only if there something you need that is not in the repos.

In that case, extract the source into ~/src/name_of_package

cd ~/name_of_package

now:

```
sudo apt-get install build-essential checkinstall
```

Then, 

	[list=number][*]Read the README and/or INSTALL file.```
gedit README
```
	[*]List the options: ```
./configure --help | less
```You may scroll through the output with up and down arrows, page up, page down ... 
	Type q to exit less.


	[*]./configure --prefix=/usr
	[*]make
	[*]sudo checkinstall -D[/list]

	[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

