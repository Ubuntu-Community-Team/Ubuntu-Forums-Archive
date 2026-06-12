---
title: "Making a Link in Applications"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by Irony on 2005-08-12
I've just downloaded the tarred Blender 2.37a from [http://www.blender3d.org/cms/Blender.31.0.html](http://www.blender3d.org/cms/Blender.31.0.html) untarred it and renamed the folder as blender. For some reason untarring it before just revealed an empty folder.

I then moved the file;

*sudo mv /home/irony/Desktop/blender /usr/lib*

This seems to be where programs are held?

I then right clicked on one of my blender files and selected Open With then browsed to the blender executable in /usr/lib/blender and applied it.

I can now open blender files in Blender 2.37a by clicking on them!

I uninstalled 2.36. I'm quite pleased because this is the first time I've issued a move command!

My question is this;

I've created a shortcut/link to blender and put it on my desktop, can I place the link or otherwise make an icon in Applications > Graphics like when I had 2.36 - its not particularly necessary, I would just like to know how to do it.

---

### Post by aysiu on 2005-08-12
Have you thought of just installing Blender via Synaptic Package Manager?

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

Otherwise, you can use SMEG to add it to the applications menu.

[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by Irony on 2005-08-12
Synaptic has Blender 2.36 but not 2.37a, unfortunately smeg isn't listed in the repositories.

---

### Post by KingBahamut on 2005-08-12
Irony smeg is in the backports, be sure you have those on your sources.list and grab it.

---

### Post by Irony on 2005-08-12
Thanks King, I assume you mean this;

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by KingBahamut on 2005-08-12
Yerps, I do.

---

### Post by Irony on 2005-08-12
Thanks I'll give it a go.

---

### Post by Irony on 2005-08-12
I added the backports to my /etc/apt/sources.list file;

[PHP]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted[/PHP]

But on opening Synaptic I get;

[PHP]W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/PHP]

Does this mean the http backports addresses are wrong?

---

### Post by jyank on 2005-08-12
You seem to have some of the addresses commented out ( # meaning commented out)

Make the sources.list look like this:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

They either hit "reload" in synaptic or type this into a terminal

```
sudo apt-get update
```

---

### Post by Kyral on 2005-08-12
And sometimes the Backports Mirror goes down :P

---

### Post by Irony on 2005-08-12
I copied and pasted what jyank posted and smeg has popped up - I still get a few missing links so I guess Kyral must be right.

Does it matter that if its gb archives rather than us (me being in UK).

Also what is the effect of removing;

*deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted*

---

### Post by aysiu on 2005-08-12
> **Irony]I copied and pasted what jyank posted and smeg has popped up - I still get a few missing links so I guess Kyral must be right.[/quote]

Here's a list of the mirrors.

[http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)

> 
Does it matter that if its gb archives rather than us (me being in UK). Shouldn't matter. There's no color (v. colour) in the SMEG application. 

[quote]
Also what is the effect of removing said:**
> / hoary main restricted* It just means when Synaptic/apt-get checks for what's available, it doesn't look for stuff from the CD-ROM drive--it pulls only from the internet.

---

### Post by Irony on 2005-08-13
Thanks to everyone!

I've installed smeg and added a Blender icon to Applications > Graphics, a nice/quick program to use.

---

