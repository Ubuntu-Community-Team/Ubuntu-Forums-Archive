---
title: "Upgrade help needed."
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by rjay45 on 2008-04-05
hey ubuntu gurus;

I've just installed ubuntu 5.10(got the cd from a client that didn't want linux) I tried to update my system and this is what came out.

W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)


I tried to add amarok(for mp3 purposes). Is the version of ubuntu i'm using an old one? Could i still be able to upgrade?

thanks.

---

### Post by mikeyphi on 2008-04-05
Sorry!!! Ubuntu 5.10 is OLD and no longer supported. Is not possible to upgrade.
You should install any one of the supported OSs but probably the latest is better (7.10 - Gutsy)
OR wait for the newest release (8.4 - Hardy) which will be out in 3 weeks!!
As a taster - the 'Beta' release can be downloaded here: [http://www.ubuntulinux.org/testing/hardy/beta](http://www.ubuntulinux.org/testing/hardy/beta)

If you need more info please ask again!

---

### Post by zvacet on 2008-04-05
Let you source list look like this 

>  
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

```
sudo apt-get update && sudo apt-get upgrade
```

After that you should be able to upgrade to Dapper.When you do it replace your source list with this one 

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Benbow on 2008-04-05
By far the easiest and most reliable way to go would be to download Gutsy ( [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download) ) on to your hard drive then transfer it as an iso image on to cd. You can then run this on your pc straight from the cd and it won't affect your existing set up. If you like what you see you can then install from there.
You will then have an up to date set up. If you are unsure as to the install process or have more questions please ask.

---

### Post by barbedsaber on 2008-04-05
yup, just get gutsy gibbon, burn the iso, boot and do a fresh install, either that or try hardy.

just keep in mind that hardy is a beta, and it may crash and burn.

---

### Post by rjay45 on 2008-04-06
Thanks for your replies guys.

Right now i'm just waiting for a friend to give me a new version of ubuntu. Internet is too damn slow these days.

i'll update you guys if anything happens..


cheers.

---

### Post by renovate on 2008-04-29
i've been trying to reinstall 5.10 not knowing that it was no longer supported. I had a problem where my graphic interface disappeared because a couple files got deleted with a package install, and I am unfamiliar with the code.

could someone tell me how to alter my package source list, so that I could follow these instructions and upgrade? thanks.

---

### Post by cybiko123 on 2008-04-29
Sure. Just type "pico /etc/apt/sources.list" (without the quotes). You will then be able to follow the instructions in the above posts.

---

### Post by renovate on 2008-04-30
thanks, i found the editor and attempted to save the file, but it tells me permission denied. I'm the root user, so how do I get permission to edit the file? It is not prompting me for a password.

If i try sudo gedit /etc/apt/sources.list I get this message:
"(gedit:9907): Gtk-WARNING **: cannot open display:"

thanks.

---

### Post by cabaro on 2008-04-30
```
sudo pico /etc/apt/sources.list
```

or

```
sudo nano /etc/apt/sources.list
```

---

### Post by renovate on 2008-05-11
Thanks, "sudo nano /etc/apt/sources.list" worked like a charm... finally making some progress.

---

