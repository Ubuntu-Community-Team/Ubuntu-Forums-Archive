---
title: "Using Repositories on an External HDD"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-05-16
Morning,

I'm currently using Dapper and XP on a dual boot laptop.

Recently I bought a copy of Feisty, and all the repositories on a set of DVD's. (No internet connection at home.)

I intend to upgrade to Feisty, and copy all of the repositories onto an external HDD.

My questions are:

1. Do I simply copy the DVD contents onto the external HDD ?
2. Presumably I then need to mount the partition where theses repositories live ?
3. How do I then make Ubuntu look at this local set of repositories, rather than the official ones ?
4. Finally, how would I go about installing from these local repos, eg how do I make WINE work ?

Thanks in advance. [-o<

---

### Post by Najand on 2007-05-16
Use the following link to learn how to use apt locally:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

### Post by WorldTripping on 2007-05-16
Thanks for that.

I've just spent half an hour getting my head around it, and it looks quite straightforward.

So, I would do something like this:

sudo mkdir /mnt/repos
dpkg-scanpackages repos | gzip > repos/Packages.gz

Then edit the `/etc/apt/sources.list' file to read:

deb file:/mnt repos/

Final question, can I comment out all of the lines in the sources.list file.

Cheers.

---

### Post by Najand on 2007-05-16
You can comment any line of the repositories you think it is not needed.

---

### Post by WorldTripping on 2007-05-17
Right,

This is officially annoying me now.

I've copied the 'Main' repository to an external HDD

It's mounted at /media/disk and I'm editing the /etc/apt/sources.list

I've put in a reference to:

deb file:/media/disk/main/dists/feisty/main/binary-i386 (which is the path to the Packages.gz file)

But the Package Manager still fails to open.

Anyone any idea ??

---

### Post by LaRoza on 2007-05-17
If you ordered the repositories on disk, like I did, you open Synaptic, the GUI.

Click "add cd-rom" or something like that, it will ask you do insert the disk then it will scan it, at the end, it will ask you to name it.

Do this for all the disks.

Now, when ever you want to install something, it will ask for the appropriate disk(s).

---

### Post by WorldTripping on 2007-05-17
Yeah, I did order the repositories on DVD, but rather than continually put them in and out of the machine, I wanted to copy them to an external HDD, and access them from there.

Any ideas what I need to put in the sources.list file, so the the Package Manager can access them ?

Cheers.

---

### Post by WorldTripping on 2007-05-18
[~bump~]

---

### Post by WorldTripping on 2007-05-18
#~ bump ~#

---

### Post by WorldTripping on 2007-05-18
[[ bump ]]

---

