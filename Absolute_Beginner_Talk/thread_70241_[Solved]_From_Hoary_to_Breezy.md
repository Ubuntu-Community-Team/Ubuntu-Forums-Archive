---
title: "[Solved] From Hoary to Breezy"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by F Junk on 2005-09-29
Hi guys,
I want to upgrade my Hoary to Breezy preview.
I have two questions:
first, I had a hard (beginner's) time configuring my wifi card and wpa settings.
is there a way I can copy *some* files, store them on the network, and paste them once my Breezy install is done?
second, do you recommend upgrading from Hoary, or a fresh Breezy install?
Thanks in advance for your answers,
F
Edit: I got my answer on the french forum. thanks anyways

---

### Post by jsimmons on 2005-09-29
[QUOTE=F Junk]Hi guys,
I want to upgrade my Hoary to Breezy preview.
I have two questions:
first, I had a hard (beginner's) time configuring my wifi card and wpa settings.
is there a way I can copy *some* files, store them on the network, and paste them once my Breezy install is done?
second, do you recommend upgrading from Hoary, or a fresh Breezy install?
Thanks in advance for your answers,
F
Edit: I got my answer on the french forum. thanks anyways[/QUOTE]


So *what* was the answer?

---

### Post by davmac on 2005-09-29
Don't know how F Junk did it, but edited my /etc/apt/sources.list and changed all mentions of "hoary" to "breezy" and commented out the backports. Then did "sudo apt-get update" and "sudo apt-get dist-upgrade", and that was it.Dave Mac

---

### Post by nitricacid on 2005-09-29
here is an example of my sources.list

(Baicly all you have to do is change anything that says hoary to the word breezy)
Just make sure you Hash out the cdrom parts if you are just going to use a terminal to update and not an actual cd.

## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908 )]/ breezy main restricted

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by F Junk on 2005-09-29
Well, there still is a debate going on on the french forum :)
Basically, as my Ubuntu is still quite new, and I didn't change much things (errrr, almost none, in fact) everybody suggested I upgrade and not resinstall.

No input on saving configuration files, though. I assume this is feasible, as my Linksys drivers are in a folder in ndsiwrapper, and the wpa_supplicant file is somewhere too. Copying them and pasting them after reinstall would not, intuitively, raise big issues?

(I mean, it's not like in Windows, where installing a program updates lots of links, registry and stuff. Here, my drivers just *sit there*...)

(I didn't not finish my Linux 101 book yet, though, so maybe I've got everything wrong)

---

