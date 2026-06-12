---
title: "Update Reload error"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by Vega on 2005-10-18
what does this mean?

---

### Post by Kapre on 2005-10-18
[QUOTE=Vega]what does this mean?[/QUOTE]

Vega - Are you Breezy? If you are. have you updated your repo to use [this]("http://www.psychocats.net/sources.html"). I've run my update when I saw your post and didn't have the problem.

K

---

### Post by Vega on 2005-10-18
[QUOTE=Kapre]Vega - Are you Breezy? If you are. have you updated your repo to use [this]("http://www.psychocats.net/sources.html"). I've run my update when I saw your post and didn't have the problem.

K[/QUOTE]

*Breezy*

Do I replace everything within my sources.list? Even the repositories of my vlc player?

---

### Post by Kapre on 2005-10-18
[QUOTE=Vega]*Breezy*

Do I replace everything within my sources.list? Even the repositories of my vlc player?[/QUOTE]

I'm not using VLC but I checked it on my Synaptic and it is there. I would suggest that you back-up your sources.list first using this: (on a terminal - click on Application ---then Accessories----then Terminal)

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

then paste the list that you've got on my previous post.

K

---

### Post by Vega on 2005-10-18
Alright I've backed up sources.list and loaded in this > ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 

but I still get the same thing after I type sudo apt-get update.

---

### Post by Kapre on 2005-10-18
Vega - I just searched thru our forum and got the results from other users who experienced the same problem but they just run sudo apt-get update and it solved the problem. Anyways, here is the [theread]("http://www.ubuntuforums.org/showthread.php?t=78033&highlight=bad+sig")

K

---

