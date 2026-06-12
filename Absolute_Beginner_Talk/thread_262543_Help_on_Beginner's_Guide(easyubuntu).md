---
title: "Help on Beginner's Guide(easyubuntu)"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by ghettosmurfmn on 2006-09-21
Hey all,

I just got done installing Ubuntu 6.06 tonight, and the very first thing I did after I booted up was go to the beginner's guide(I'm very new to Linux) located at the url below:

[http://ubuntuguide.org/wiki/Dapper#Getting_Started](http://ubuntuguide.org/wiki/Dapper#Getting_Started)

I started off in the "Repositories" section, and then moved on down through the tutorial until I got to "Add-on Applications" at which point I tried to use easyubuntu. I got it going and checked all the boxes for the stuff I wanted to install, and after hitting ok a few moments pass and I get this message:

```
The follow problems were found on your system:

W: Duplicate sources.list entry http://packages.freecontrib.org dapper/free Packages (/var/lib/apt/lists/packages.freecontrib.org_plf_dists_dapper_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.freecontrib.org dapper/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_plf_dists_dapper_non-free_binary-i386_Packages)
```

So I click Ok, another moment passes, and an error box pops up saying "Could not apply changes! Fix broken packages first."

I have no idea what it's talking about. How can I have broken packages already? Where did I go wrong?

Appreciate any help here!

---

### Post by aysiu on 2006-09-21
Maybe you actually have duplicate sources in your /etc/apt/sources.list.

Paste this command into the terminal: ```
sudo nano -B /etc/apt/sources.list
``` Delete (Control-K) any duplicate lines. Then, save (Control-X, Y, Enter). Then do ```
sudo aptitude update
```

---

### Post by tagra123 on 2006-09-21
> **ghettosmurfmn said:**
> Hey all,

I just got done installing Ubuntu 6.06 tonight, and the very first thing I did after I booted up was go to the beginner's guide(I'm very new to Linux) located at the url below:

[http://ubuntuguide.org/wiki/Dapper#Getting_Started](http://ubuntuguide.org/wiki/Dapper#Getting_Started)

I started off in the "Repositories" section, and then moved on down through the tutorial until I got to "Add-on Applications" at which point I tried to use easyubuntu. I got it going and checked all the boxes for the stuff I wanted to install, and after hitting ok a few moments pass and I get this message:

```
The follow problems were found on your system:

W: Duplicate sources.list entry http://packages.freecontrib.org dapper/free Packages (/var/lib/apt/lists/packages.freecontrib.org_plf_dists_dapper_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.freecontrib.org dapper/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_plf_dists_dapper_non-free_binary-i386_Packages)
```

So I click Ok, another moment passes, and an error box pops up saying "Could not apply changes! Fix broken packages first."

I have no idea what it's talking about. How can I have broken packages already? Where did I go wrong?

Appreciate any help here!


sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_didntwork
sudo cp -p /etc/apt/sources.list_backup /etc/apt/sources.list
apt-get updates


This will get you back to where you started before making changes.

Then using synaptic: Panel Menu : System > Administration > Synaptic Package Manager

Add your repositories.

Click on Settings > Repositories

Until you are familar with the sources.list file I'd suggest using the gui.

I don't believe the universe and multiverse packages are supported by ubuntu but sometimes there is just a program you need or want in these repositories.

---

