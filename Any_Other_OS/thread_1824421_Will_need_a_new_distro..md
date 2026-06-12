---
title: "Will need a new distro."
date: 2011-08-13
forum: Any Other OS
---

### Post by Number3124 on 2011-08-13
I've been doing my research, and I am pretty sure that I will need a new distro when Oneiric Ocelot (11.10) is released. I hated the Unity interface and am currently running Natty in Classic Sans Effects with a port of the 7.04 theme which nicely imitates GNOME 2 (my favorite GNOME). As far as I know the Unity interface will become more prominent in 11.10 and the Classic desktop will be implemented through GNOME 3 which I also do not like at all.

I'd like a distro that avoids the Unity desktop and GNOME 3. I've been looking at Fedora, but it already seems to have jumped on GNOME 3. I've also been looking at Debian, Mandriva, Mint, and several others. Would it be possible to revert to GNOME 2 or would I have to move over KDE or Xfce? Thanks for the help.

---

### Post by Kromgol on 2011-08-13
Gnome2 is still widely available in most repositories, just uninstall Gnome3 and get Gnome2 instead.

---

### Post by Number3124 on 2011-08-13
Okay, so that would be possible. I'm assuming I could just do something like "sudo apt-get install GNOME2"? Any recommendations on a new distro? I am interested in trying something new out. I've heard good things about Fedora and Mandriva.

---

### Post by Kromgol on 2011-08-13
Not all distros use the same package manager, for example both Fedora and Mandriva uses RPM, while distros based of Debian and such use apt.

I would recommend installing a lightweight Debian which is with no GUI, and you can from there install a desktop enviroment. But that means you will need to do most things yourself, like install xorg-server, setting up video drivers etc.

Arch Linux is also nice.

If you now want a working GUI from the beginning, go with Debian. I still think they are using Gnome2 as their primary DE.

---

### Post by Number3124 on 2011-08-13
I was thinking something along those lines. Thanks for the help guys.

---

### Post by Kromgol on 2011-08-13
Guys? Did i just become multiple people? :D
Anyway, no problems. Just remember that those are my choice, i'd recommend you look into things yourself and then decide :)

---

### Post by Number3124 on 2011-08-13
*Looks back at thread* Oh dear... Well thank you then.

---

### Post by snowpine on 2011-08-13
Ubuntu 10.04 will support Gnome 2 through April 2013, Debian Squeeze for another couple of years, Red Hat for another 5 years, etc.

---

### Post by NightwishFan on 2011-08-13
Gnome 2 will not be officially supported no matter what distro you choose. Your best bet if you want to keep using it is to find a distribution that has very long support cycle like Debian (3 years) Ubuntu LTS (three years). Or CentOS, Scientific, Red Hat (longer). This just means you will have it longer not that they will continue development on it.

There is a project to keep Gnome 2 alive but I am willing to bet it will be a bit disruptive to actually install it on some distros. (I could be wrong though, time will tell).

As for Gnome 3 it does have a fallback interface. If it improves a lot of users might be in luck if they like the panel interface. Wait for Gnome 3.2 and 3.4 to see how that goes. Also I am sure Unity/Unity2d will improve as well.

Distro hopping is not the answer. If you do not like Gnome 3/Unity, you will probably have to switch to another environment.

---

### Post by IWantFroyo on 2011-08-13
-Debian 6
-CentOS 6
-Ubuntu 10.04
-Ubuntu derivatives. A lot of them are keeping GNOME 2 (LM, eOS, etc.).

---

### Post by craig10x on 2011-08-13
You might be interested to know that as of Linux Mint 12, it will be going Gnome3 WITHOUT unity nor shell...it will have the same familar one panel on bottom and mint menu it has always had :)

Clem, who heads mint has no plans to use either unity or the shell...on Linux Mint Main Edition (ubuntu based) or LMDE (debian testing based version)...

---

### Post by drawkcab on 2011-08-15
XFCE 4.8 is the natural GNOME 2.x alternative.  It wouldn't hurt to start playing around with Xubuntu.

I love Mint except for the way in which it hijacks google searches.

---

### Post by drawkcab on 2011-08-15
And so it begins!  MATE, the GNOME 2 fork!

[http://matsusoft.com.ar/redmine/projects/mate](http://matsusoft.com.ar/redmine/projects/mate)

---

### Post by F.G. on 2011-08-15
hey, so, my two cents:
i used open Suse for a while,  which is .rpm (novell/red hat based) and would recommend it, though if you want to stick to something similar to ubuntu it may be advisable to stick with a debian based distro.  also i used linux Mint for a couple of years and found it to be a really good distro for out of the box usability, compatibility and style (though i really didn't like mint 10). Mint also has a xfce and kde releases.

as has been pointed out picking a DE and then finding a ubuntu derivative for your (and probably my own) purposes may be the way to go.  open-box is good (cruchbang is a nice openbox distro, though a bit experimental), similarly black-box, lxde and numerous other lightweight alternatives. also you can always just use debian and do the legwork for the desktop environment yourself (i might be heading this way myself).

good luck with your search.

---

