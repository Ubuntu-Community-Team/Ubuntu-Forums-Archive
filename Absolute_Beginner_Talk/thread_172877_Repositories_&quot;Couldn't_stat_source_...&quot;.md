---
title: "Repositories &quot;Couldn't stat source ...&quot;"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-05-09
Are these repositories dead/down? When I run Synaptic I get the following error message:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

---

### Post by RavenOfOdin on 2006-05-09
That may be because they're down, or your Internet connection went dead. 

BTW. . .I strongly recommend against installing anything from theli.free.fr, or for that matter any unofficial repository. This goes double for Synaptic, which requires you to run it as superuser.

Go into your "Manage Repositories" list in Synaptic, and get that entry out. Now.

---

### Post by aysiu on 2006-05-09
[QUOTE=RavenOfOdin]
This goes double for Synaptic, which requires you to run it as superuser.[/QUOTE] Every command or application that invokes *dpkg* to install applications requires you to run it as superuser--Adept, Synaptic, apt-get, gnome-app-install, aptitude...

---

### Post by RavenOfOdin on 2006-05-09
Of course they do. This isn't being stated for my benefit. ;)

---

### Post by aysiu on 2006-05-09
[QUOTE=RavenOfOdin]Of course they do. This isn't being stated for my benefit. ;)[/QUOTE] I just wanted to clarify. The way you stated it could be easily misinterpreted to mean that Synaptic invokes the superuser, but other applications using the same repositories don't.

---

### Post by Mark_in_Hollywood on 2006-05-09
[QUOTE=RavenOfOdin]That may be because they're down, or your Internet connection went dead. 

BTW. . .I strongly recommend against installing anything from theli.free.fr, or for that matter any unofficial repository. This goes double for Synaptic, which requires you to run it as superuser.

Go into your "Manage Repositories" list in Synaptic, and get that entry out. Now.[/QUOTE]

Internet connection working fine, all other repositories working as reported/configured.

Synaptic always requires a password when called from System/Admin/Syn... Is this not the way it is supposed to be?

Now I'm scared. I had replaced my official repositories with the ones pasted at:

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) (see below)

I knew they had "non" official repositories, but I can't find where the theli.free.fr, came from. Is somebody sending me harmful code?

viz:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

---

### Post by SkyNet2029 on 2006-05-10
From what I could tell from this: [http://theli.free.fr/packages/]("http://theli.free.fr/packages/")  this is the audio codecs/fix midi in gnome 
portion of the script.

As for the unable to stat source, I get the same thing here..so I went and commented it out of my list. ( I don't use audio here anyway ;-) )

---

### Post by Mark_in_Hollywood on 2006-05-10
BTW. . .I strongly recommend against installing anything from theli.free.fr, or for that matter any unofficial repository. This goes double for Synaptic, which requires you to run it as superuser.

Go into your "Manage Repositories" list in Synaptic, and get that entry out. Now.

If you would be so kind as to state your objection, please. I need to know about "technical" and not legal/moral/ethical problems with my computer. If there is a "technical" problem with those repositories, please say so.

---

