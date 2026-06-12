---
title: "How to operate the GParted terminal"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Jonnothin on 2007-08-07
Ok GParted starts up but I don't know how to operate the terminal.

Someone tell me how to do this.

---

### Post by skymera on 2007-08-07
for partition editing i used gparted...its gui.

i think using gui is important unless you know what you are doing.

its in repos

---

### Post by Jonnothin on 2007-08-07
But I just burned GParted because I was told I could use it to delete my vista partition and put ubuntu on.

So what are you talking about?

---

### Post by benerivo on 2007-08-07
You didn't need to have a separate GParted CD as this program comes as part of the Ubuntu CD. Just download and burn Ubuntu, and then load the CD. Choose the install icon on the desktop, and the installation process will include the GParted program so that you may change your partitions. See this [excellent guide for installing Ubuntu]("http://www.psychocats.net/ubuntu/installing"). Personally i would keep your Vista, as it is doing no harm sitting on your pc, and you did pay for it. At the least you may use it as a temporary backup OS.

---

### Post by Jonnothin on 2007-08-07
the other ubuntu discs won't get to the desktop they get screwy before they do.

---

### Post by benerivo on 2007-08-07
OK, although just removing an existing OS may not fix the problem with the Ubuntu CD failing to load in to the desktop. You can still use the link i posted as it includes a guide for using GParted to change the drives (see the bit entitled "Dealing with Partitioning").

It may also be useful to post any information you were given as to why the Ubuntu CD failed, including your hardware specs. I would do this in another post, so that the title thread is relevant.

---

### Post by cobrn1 on 2007-08-07
Are you saying the live CD won't load properly? If so, how far does it get before it freezes?

This could be due to graphics incompatability, or a slow pc (my 733Mhx, 128Mb RAM can't run the live CD and freezes just when it's starting the graphical interface, I get the cross and then if hangs forever - thr alternate install CD works fine tho...)

Anyway, we need to know what your hardware specs are and when the disc freezes (and is it the live cd disc?)


However, to use Gparted it has a graphical interface, which should open when it loads the desktop. If not then click on the Gparted icon on the desktop to load it up. THat will give you a graphical representation fo your harddrive, and you can click and select what to do with the partitions. THen just right-click on the vista partition, choose delete, make a large partition for ubuntu, and make a swap partition too (about a gig should do).

---

### Post by Jonnothin on 2007-08-10
I found out what the problem was and got it to work.

---

