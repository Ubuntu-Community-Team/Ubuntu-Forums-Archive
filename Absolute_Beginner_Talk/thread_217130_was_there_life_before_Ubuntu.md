---
title: "was there life before Ubuntu?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by alan yeates on 2006-07-16
four installs and four crashes, two I have traced to trying to configure X with the command from the last release, given in a Wiki, but the first and present problem was after downloading the updates shown, many GUI's won't accept password or won't appear at all and I can only get root on the console. This means I am unable to install, say Turboprint since it needs root privileges, though if there is another way I'd love to know:evil: , I can run most other stuff OK. (I can get Synaptic from the terminal however) Is there a less buggy desktop out there perhaps?

---

### Post by patrickfromspain on 2006-07-16
there's no problem with gui's.. the problem is you don't know how to open ;)

In turboprint case: cd /dir/to/turboprint/folder and then sudo ./setup

and that should do the trick.

---

### Post by alan yeates on 2006-07-16
All GUI's opening fine until updates downloaded, and can't get into Turboprint without root, since it has to delete existing printers. Would there be a workaround using The Turboprint website as a repository?

---

### Post by patrickfromspain on 2006-07-16
no, that isn't possible.

Anyway, the turboprint setup page, you can open it by typing sudo xtpsetup in a terminal.

---

### Post by alan yeates on 2006-07-16
Will give that a go, its funny that I have nearly the same setup as yourself except for Nvidia card (now working). If I could get my Canon ip3000 working I could print out a lot of helpful stuff! :-k

---

### Post by alan yeates on 2006-07-16
Afraid things are going from bad to worse, can't sudo synaptic now, message reads: (synaptic:5565): Gtk-WARNING **: cannot open display::confused:

---

### Post by Sef on 2006-07-16
Check to see if you have the same problem with a LiveCD.  If you do, then there is a conflict with the hardware most likely.  If not, then likely the install was corrupted.

---

### Post by Ptero-4 on 2006-07-16
It seems you got a f*ked up gksudo package, probably from the updates, that explains why after the updates you became unable to autenticate to root in GUI apps.

---

### Post by Dr. Nick on 2006-07-16
> **alan yeates said:**
> Will give that a go, its funny that I have nearly the same setup as yourself except for Nvidia card (now working). If I could get my Canon ip3000 working I could print out a lot of helpful stuff! :-k

Are you trying to get turboprint for your ip3000?

I have a Ip3000 aswell and didnt need turboprint, Instead I used the included bjc-7000,bjc800 driver that was included in ubuntu and the printer works just fine that way, may be worth a shot.

---

