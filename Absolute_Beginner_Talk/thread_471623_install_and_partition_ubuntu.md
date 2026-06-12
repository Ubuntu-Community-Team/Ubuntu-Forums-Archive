---
title: "install and partition ubuntu?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by jagguy on 2007-06-12
Hi,

I got ubuntu from a pc mag dvd. I downloaded it and tested the media and it came up fine.

I burnt a cd and it seems to work but i am confused about partitining.
I have a c: with winxp 30g and another hd f: with 80g. This has a partition of 60g for windows and the other 20g for linux.

That 20g has other failed linux installs on it which i dont need. Now how can i load the whole ubuntu on that 20G space and have it dual-boot or boot linux from a cd?
Do I need to create further partitions in thAT 20g or will ubuntu do this?

I dont want to touch the other indows partitions.

What can i do?

---

### Post by overdrank on 2007-06-12
> **jagguy said:**
> Hi,

I got ubuntu from a pc mag dvd. I downloaded it and tested the media and it came up fine.

I burnt a cd and it seems to work but i am confused about partitining.
I have a c: with winxp 30g and another hd f: with 80g. This has a partition of 60g for windows and the other 20g for linux.

That 20g has other failed linux installs on it which i dont need. Now how can i load the whole ubuntu on that 20G space and have it dual-boot or boot linux from a cd?
Do I need to create further partitions in thAT 20g or will ubuntu do this?

I dont want to touch the other indows partitions.

What can i do?

Hi during the installation you will come to the gpartition and there you can select the partition with the failed linux on it. Then install there and create a swap partition ( I believe there should be a swap if you have had linux on there) This link may help explain it better.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Good Luck!:popcorn:

---

### Post by jagguy on 2007-06-12
How can i create a cd boot instead of a deafult install of ubuntu?

I get the problem must create a home partition as the swap is there.
Do i need to create another partition within that 20g space for  home 

That article didnt explain this point which the installer is stopping me from installing .

---

### Post by ccfjeff on 2007-06-12
> **jagguy said:**
> How can i create a cd boot instead of a deafult install of ubuntu?

If I'm understanding your question correctly, you can download a LiveCD from [Ubuntu home]("http://www.ubuntu.com/").

[Desktop version]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition")

---

### Post by jagguy on 2007-06-12
hi,

No your not understanding me.
I have the liveCD and it does work.

I need install help because I am unsure about partitions.
I have wixp on my pc and have 2 HDs. The second HD has 20g fee space whaere i want to install ubuntu and the 1st HD has winxp and no more room.

The installer asks where to install /home parttiton which there is nowhere because the 20G place isnt split up into 3 partitions.

Do I need to run Gparted to do this, that is create 3 partitons in this 20G area i want linux.

Now i read links on this and no i cant get an answer.
I didnt want to install ubuntu alongsid windowsxp in the same partition on my 1st HD as i have on 9G left on the master HD?

---

### Post by ccfjeff on 2007-06-13
> **jagguy said:**
> hi,

No your not understanding me.
I have the liveCD and it does work.

I need install help because I am unsure about partitions.
I have wixp on my pc and have 2 HDs. The second HD has 20g fee space whaere i want to install ubuntu and the 1st HD has winxp and no more room.

The installer asks where to install /home parttiton which there is nowhere because the 20G place isnt split up into 3 partitions.

Do I need to run Gparted to do this, that is create 3 partitons in this 20G area i want linux.

Now i read links on this and no i cant get an answer.
I didnt want to install ubuntu alongsid windowsxp in the same partition on my 1st HD as i have on 9G left on the master HD?

Hi jagguy, sorry about all of the problems and aggravation you are having.  I'm afraid I'm a newbie and in fact a step behind you.  I've gotten the LiveCD to work OK on a couple of computers and a "DamnSmall Linux LiveCD to work on an old computer, but I haven't actually installed any to the hard drives yet.  I've been reading up on it as you have.  I can throw a few random thoughts out there that might be of help, but if not, maybe it'll bump this up to where someone who can better help you will see it.

In [bodhi.zazen's partitioning howto]("http://ubuntuforums.org/showthread.php?&t=282018") he states that /home is optional:

[SIZE=2][COLOR=DarkRed]_Options_.[/COLOR][/SIZE][COLOR=DarkRed]

_/home_: This is helpful if you need to re-install Ubuntu. /home stores user data and user configuration files.

Limitations:[/COLOR][LIST=1]
[*][COLOR=DarkRed]/home does not save all of the installed applications you have installed or removed beyond the base install.[/COLOR]
[*][COLOR=DarkRed]If you boot multiple distros those user config files can conflict.[/COLOR][/LIST][COLOR=DarkRed]
_/data_:  This is helpful and I use this in favor of /home.

Why?[/COLOR][LIST=1]
[*][COLOR=DarkRed]First, I boot multiple distros and user configuration files in /home can conflict as above.[/COLOR]
[*][COLOR=DarkRed]Those user config files are not "mission critical" to back up. They will be regenerated if deleted, although you will loose your application preferences.[/COLOR]
[*][COLOR=DarkRed]Backup /home to /data and you can restore /home.[/COLOR]
[*][COLOR=DarkRed]Data partition can be shared with other OS (Windows or other distro's) easier then /home.[/COLOR][/LIST][COLOR=DarkRed]
You can, of course, mount your data partition as any name (mount point) you like.[/COLOR]

[Psychocat's page on deciding how to set up the partitions]("http://www.psychocats.net/ubuntu/partitioning") shows quite a few different ways to do it and explores some of the advantages and disadvantages.  One of his diagrams (you can click on them for a larger image) shows a Windows partition, a Ubuntu partition and a swap file for Ubuntu:

[IMG]http://img379.imageshack.us/img379/2770/partitioning2ur3.png[/IMG]

Those sizes are relative of course, but it appears that you do not necessarily *have* to have a /home partition.  Psychocat's preferred setup would have it, however (and no Windows):

[IMG]http://img379.imageshack.us/img379/8700/partitioning7sa2.png[/IMG]

It sounds like the setup you are trying to set up would include a Windows partition and a /home partition in addition to the Ubuntu root(?) partition:

[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]

I'm wondering if I might not be better off without the home partition, however:

[IMG]http://img379.imageshack.us/img379/2770/partitioning2ur3.png[/IMG]

It seems like it might save a little space (if the "root" partition for the Ubuntu OS isn't fully utilized).  From whatbodhi.zazen wrote, it doesn't sound like the extra partition would keep down any fragmenting for the OS.  I'm guessing it would mainly be a security issue of being able to give multiple users different degrees of access to the various partitions.  I'm a single user, though, so I don't know if that would apply to me.

I imagine I could just set up folders for /programs /pics /docs etc. and could still back them up individually if I liked.

With respect to the partitioning, I believe you do need to use GParted or a similar partioning program.  As I understand it GParted comes with the Distro and seems to work well for most people.

As to booting from a CD, I guess you must have figured out how to do that with the LiveCD, but I doubt that would be the way to go if you installed it on your hard drive as well.

It sounds to me like after it is all set up you will be able to choose which operating system to use from a boot up menu after you start the computer.  There are apparently several options there as well.  You might find a little help on that from the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/").

It mentions setting up a [Gag Boot Manager CD-ROM or floppy disk]("http://users.bigpond.net.au/hermanzone/p12.htm") to help you boot up if something goes awry.  The [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") is apparently another similar emergency disk.

Anyway, good luck with it all.  Hopefully all will go well and you can blaze a trail for me.  ;)

---

### Post by ccfjeff on 2007-06-13
Oops.  Duplicate.  Sorry about that!

---

### Post by ccfjeff on 2007-06-13
**[SIZE=4]Preparing for System Failure ... And Recovering Quickly[/SIZE]**
Submitted by chadm on Sat, 2007-04-28 20:38.     

[http://linuxappfinder.com/blog/preparing_for_system_failure_and_recovering_quickly](http://linuxappfinder.com/blog/preparing_for_system_failure_and_recovering_quickly)

Despite the improvements made each year by GNU/Linux, KDE, and GNOME, recovering from failure is one of the recurring themes many new users struggle with. Why aren't we making it easier to prepare for, and recover from, failure? Here are some proposals to make recovery less painful. ...

---

