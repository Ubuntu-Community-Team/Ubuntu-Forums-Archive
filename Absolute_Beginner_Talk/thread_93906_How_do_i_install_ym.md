---
title: "How do i install ym?"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by johnxxv on 2005-11-23
i download yahoo messenger for debian and when i tried to install it by 
typing 
   /Desktop # dpkg -i ymessenger_1.0.4_1_i386.deb
i get the following
   (Reading database ... 58045 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not configured yet.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

----
it seems i need to download packages for dependencies, but i dont know how. i tried to download for eg libgdk-pixbuf2, but i get more dependencies when i try to install it.

Help.

---

### Post by sabitha on 2005-11-23
try with :

# apt-get -f install

maybe that can fix that

sorry for my english ;)

---

### Post by xmastree on 2005-11-23
> **johnxxv]dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on [COLOR="Red"]libgdk-pixbuf2[/COLOR] (>= 0.13.0) said:**
> libglib1.2[/COLOR] (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on [COLOR="Red"]libgtk1.2[/COLOR] (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on [COLOR="Red"]libssl0.9.6[/COLOR]; however:
  Package libssl0.9.6 is not installed.
Open synaptic, search for the packages (highlighted in red) that /YM is looking for and install them first. Any dependencies will be automatically taken care of by Synaptic.

Then try installing YM again.

Having said that, do you really need Yahoo Messenger? Gaim is much nicer...

---

### Post by ndtoan13 on 2005-11-30
[QUOTE=sabitha]try with :

# apt-get -f install

maybe that can fix that

sorry for my english ;)[/QUOTE]
I have the same problem with johnxxv, and I do the same as sabitha said but It can not install, I look up at synaptic, the package need to install YIM is libssl0.9.6, but my Ubuntu 5.1.0 have installed libssl0.9.7, and there is no libssl0.9.6 to install YIM!! :confused: 

I also try GAIM, but it require GLIB to run, and GLIB is not in synaptic!!
Do anyone have installed Gaim? Please tell me how to install.

Thank you.

---

### Post by Orunitia on 2005-11-30
You should already have gaim installed on a default ubuntu install. Look under Applications > Internet > Gaim

---

### Post by xmastree on 2005-11-30
[QUOTE=ndtoan13]I also try GAIM, but it require GLIB to run, and GLIB is not in synaptic!![/QUOTE]Gaim should be part of the default Gnome desktop. Glib is certainly in synaptic, how did you search? The packages are mostly called libglib*

If you don't have Gaim, find it in synaptic and it should install any libraries it needs.

---

### Post by thinhlegolas on 2005-12-01
From what I know, YM for Linux is not really stable yet. Gaim is the current best alternative... might wait around a while more for the yahoo folks to improve Linux YM

---

### Post by BatsotO on 2005-12-01
just in case that you install unix ym for web cam, they dont have it yet. Standard gaim dont have it too. Try gaim vv or gyach, they do have web cam service.

---

### Post by ndtoan13 on 2005-12-01
Thank you for your help, I now find Gaim.

---

### Post by ndtoan13 on 2005-12-01
Thank you for your help, I now find Gaim.

---

