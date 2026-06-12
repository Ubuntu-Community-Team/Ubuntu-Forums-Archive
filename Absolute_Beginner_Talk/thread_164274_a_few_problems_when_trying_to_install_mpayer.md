---
title: "a few problems when trying to install mpayer"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by ukemike on 2006-04-22
I am totally new to the linux experience.  I have this hand-me-down pc that I have installed edubuntu on dual boot with the win98 that it came with.  Currently this PCs main job is playing DVDs for my son.  I am trying to get it setup do do this in ubuntu so I never have to look at win98 again.

When I run Synaptic Package Manager it tells me I have a broken package.  When I filter the list for broken it lists "edubuntu-desktop  v0.32"  I've marked it for re-installation and had it "appy marked changes".  It also marks a japanese font package for install and I cannot unmark it.  I get this error:

W: Failed to fetch cdrom:[Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/t/ttf-kochi/ttf-kochi-mincho_1.0.20030809-3_all.deb
  MD5Sum mismatch

and it never gets around to the desktop reinstall.  

==========================
my other problem

I search within Synaptic for mplayer (I ran easyubuntu script earlier today).  I found one labled -586 which seems correct since this old pc has a pentiumIII.  When I try to mark it for install I get a message saying various lib* files need to be marked for install so I hit "mark" and I get this error message:

mplayer-586:
 Depends: libdirectfb-0.9-22  but it is not installable
 Depends: libggi2 (>=1:2.0.5) but it is not installable
 Depends: libjack0.80.0-0 (>=0.99.0) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: xmms (>=1.2.10+cvs20050209) but it is not installable

I'm kind of at a series of dead ends.

---

### Post by jazzmuzik on 2006-04-22
Have you fiddled with your repositories? I get the impression that a repository is missing.

---

### Post by ukemike on 2006-04-22
No.  I'm afraid I don't know what a repository is.  That's the kind of thing I was trying to say when I said I am totally new to linux.  Yo say nada.  Yo soy newbie!!

---

### Post by jazzmuzik on 2006-04-22
I'm at a loss.

---

### Post by kh4nh on 2006-04-22
[QUOTE=ukemike]No. I'm afraid I don't know what a repository is.[/QUOTE]

"A repository is a central place where data is stored and maintained. A repository can be a place where multiple databases or files are located for distribution over a network, or a repository can be a location that is directly accessible to the user without having to travel across a network" - Wikipedia

More infos can be found here: [http://www.ubuntu.com/ubuntu/components]("http://www.ubuntu.com/ubuntu/components")

---

### Post by r4ik on 2006-04-22
Perhaps this could be of any help,

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Good luck !

---

### Post by ukemike on 2006-04-22
okay I added "universe" to my repositories and tried again and it is installed!  Naturally it doesn't seem to be working but let me fiddle with it for a while until I have a specific question to ask.  Thanks.

Mike

---

