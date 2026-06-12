---
title: "apologies for being an Ubun00b"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by marshall1001 on 2008-04-10
I;ve just installed Ubunto 8.04 beta using Wubi. This is a minor thing, however it does seem to get on my nerves quite a bit. Every time I log into Ubuntu my desktop wallpaper has gone, to be replaced by a block colour, and the shortcut I created to access a sub-folder on my external hardrive has gone.

Also, I can't set my keyboard to the UK version.

Help please? Cheers

---

### Post by guilly on 2008-04-10
If your new to linux/ubuntu maybe it isn't such a good idea to use a beta version ... you might want to wait until the official version is released. In the mean time I would download Gutsy and see if your problems are addressed .

---

### Post by Hospadar on 2008-04-10
Well you could certainly try using 7.10 instead, although from my experience, 8.04 is pretty much stable.

What I'd really suggest is backing up your important windows files, dump the wubi installation, and try a normal install, I suspect it would clear up your problems right away without damaging your windows install.  Just make sure of a couple of things:
1) Defrag your windows drive several times before you start the process
2) Before you install, use gparted (off the livecd) to shrink down your windows partition leaving enough space (bare minimum 3 gb) for your ubuntu installation.  To open gparted,  Alt-F2, type "sudo gparted", then right click the windows partition->resize, and drag it to the size you want, then say "apply" and don't touch your machine till it's done.  It can take a long time.
3) Now start the installer, when you get to the partitioning part, read the options carefully, you want to install into the free space on the drive you just created.  Make sure you don't wipe your windows installation (unless you want to!).

---

