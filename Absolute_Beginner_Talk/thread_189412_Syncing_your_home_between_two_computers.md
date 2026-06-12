---
title: "Syncing your /home between two computers?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Master One on 2006-06-05
Let's say, you have a workstation and a laptop, both running (k)ubuntu, is there an easy way to sync your /home folder between the two?

Sorry if this should be obvious, but I am completely new to (k)ubuntu, and I'm just starting to gather information (have no working setup yet).

---

### Post by adam.tropics on 2006-06-05
You should do some reading on a program called 'rsync' which sounds like it's what you're after.

Incedentally I had a little look around and found [this. ]("http://www.cis.upenn.edu/~bcpierce/unison/")Now thtat looks neat.

---

### Post by Master One on 2006-06-05
[QUOTE=adam.tropics]You should do some reading on a program called 'rsync' which sounds like it's what you're after. Incedentally I had a little look around and found [this. ]("http://www.cis.upenn.edu/~bcpierce/unison/")Now thtat looks neat.[/QUOTE]
I was hoping for a ready to use solution, which just needs to be installed, and can be managed directly from the desired DE, without the need to fiddle arround in a console.

Unison seems the be the right direction, but unfortunately the link to the debian package ([http://packages.debian.org/testing/net/unison.html](http://packages.debian.org/testing/net/unison.html)) is dead.

---

### Post by adam.tropics on 2006-06-05
grsync

It's in the repos. Basic, but works.

---

### Post by Master One on 2006-06-05
Not bad. I just took a look at the ubuntu package online database, unfortunately there seem to be no KDE frontend available for rsync. I also found unison in the package db, but again only with gtk-fontend. Not a big deal, but KDE is my preferred DE (and kubuntu my edition of choice).

---

### Post by adam.tropics on 2006-06-05
[http://sourceforge.net/projects/qsync/]("http://sourceforge.net/projects/qsync/")

---

### Post by Master One on 2006-06-05
[QUOTE=adam.tropics][http://sourceforge.net/projects/qsync/]("http://sourceforge.net/projects/qsync/")[/QUOTE]
Anyone here able to build a package?

---

### Post by Kimm on 2006-06-05
Why cant you build it?

---

### Post by Master One on 2006-06-05
[QUOTE=Kimm]Why cant you build it?[/QUOTE]
I am completely new to the (k)ubuntu world, I'm a just a user being sick of that M$ crap, and I still even don't have a working (k)ubuntu setup (waited for dapper, but had no time by now to convert my Gentoo boxes over). I'm coming from Gentoo Linux, because I need something more userfriendly (not in the mood for compile-sessions needing days any more). I may have a look at things not available in the repositories, once I have all up and running, but I thought, this definitely should be something of interest for lots of other people as well.

---

### Post by musicinmybrain on 2006-06-05
I use JFileSync ([http://jfilesync.sourceforge.net](http://jfilesync.sourceforge.net), not in the repositories but it's Java, so you won't have to compile) in combination with sshfs (available in the repositories, HOWTO [here]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")). I use a script like this to mount the remote filesystem and open JFileSync in one step, and I put a link to it in my (GNOME, in my case) menu:

```

#!/bin/bash

sshfs user@123.45.67.89:/home/user /media/remotehome
java -jar /usr/local/JFileSync/lib/jfs.jar $*

```

Also, is there any particular reason you don't want to use something with a GTK frontend? I know you prefer KDE, but is it a big deal to have one program use the GTK libs? I suppose JFileSync has the "advantage" of being neither GTK- nor QT-based.

---

### Post by Master One on 2006-06-06
Thanks for the hint, musicinmybrain, that's cool as well. I have nothing against using a GTK-app in KDE, but of course I prefer a QT-equivalent, if available.

---

