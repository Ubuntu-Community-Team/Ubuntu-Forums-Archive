---
title: "Ubuntu Server install - partitioning"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by riverman on 2006-09-11
Hi all. I'm installing Ubuntu 6.06.1 server on an i386 box. I've got through the following steps of the installation:

Language (English)
Location (UK)
Keyboard (British English)
..
..
Network Config (DHCP)
..
..
Detect Hardware

I've got a small Windows install that I want to keep, so when I get to 'Partition Disks' I select 'manually edit partition table'. There's only one partition on my disk; I want to make it smaller and then use the free space to create a new partition for Ubuntu. My problem is, when I try to set a new size for the partition, the installer doesn't seem to register it. I enter the new size, continue, and am returned to the partition summary screen which still shows me the original partition sizes. 

Aditionally, I seem to be getting the screen that asks me to confirm whether I want to 'write the changes to disk and resize the partition' *before* I get to the screen where I specify what size the existing partition should be shrunk to.

Am I doing something wrong, or missing something, or is there a problem with the partitioner?

Notes: 

(1) There's no option to 'resize and use the freespace' in the partitioner menu - from the guides I read I'd expected this option to be there, so I'm just pointing it out to save people suggesting it and then having me say 'nope!'.

(2) If I can't find a way to get things working in the next few hours, I'm gonna go ahead and just reformat the whole disk, but I'd still be interested to know what's going on for future reference.

Here's hoping for replies that are shorter than my question :)

---

### Post by bodhi.zazen on 2006-09-11
[list=number]
[*]First defragment your windows partition from windows.
[*]Boot live cd.
[*]Run Gparted -> resize windows partition.
[*]Install ubuntu into newly created free space.[/list]

[Graphical Install Guide](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by riverman on 2006-09-11
Thanks.
> **bodhi.zazen said:**
> 
First defragment your windows partition from windows.

Done (from Windows).
> 
Boot live cd.

Unfortunately, I'm not using the live cd; I'm using the Server cd instead (ubuntu-6.06.1-server-i386.iso). I've tried the live cd, and it was way to slow; gnome took about half and hour just to load.

---

### Post by bodhi.zazen on 2006-09-11
> **riverman said:**
> Thanks.

Done (from Windows).

Unfortunately, I'm not using the live cd; I'm using the Server cd instead (ubuntu-6.06.1-server-i386.iso). I've tried the live cd, and it was way to slow; gnome took about half and hour just to load.

As far as I know, no can do with sever CD. :(

Try GParted CD:

[Gparted](http://gparted.sourceforge.net/livecd.php)

---

### Post by bodhi.zazen on 2006-09-11
You do know a server install is CLI. No GUI, although you can install one?

Perhaps Xubuntu, Fluxbuntu, Puppy, SLAX, or DSL would be better.

---

### Post by riverman on 2006-09-12
> **bodhi.zazen said:**
> You do know a server install is CLI. No GUI, although you can install one?

Perhaps Xubuntu, Fluxbuntu, Puppy, SLAX, or DSL would be better.

Yeah, I chose the server version specifically because I wanted a simple (and smaller) install. The PC is going to be a file server on my local net so I don't want a GUI at the moment :)

Thanks for the advice; in the end I decided just to wipe the windows installation and use the whole hard disk. The Ubuntu installation went fine from there on.

(PS: I also went for the CLI for nostalgia value; I started computing in DOS and I enjoyed the simplicity!)

---

### Post by bodhi.zazen on 2006-09-12
I use a server install myself  :cool:

Just wanted to forewarn you.

---

