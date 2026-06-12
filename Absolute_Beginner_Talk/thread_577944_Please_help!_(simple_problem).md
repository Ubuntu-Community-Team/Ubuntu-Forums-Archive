---
title: "Please help! (simple problem)"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-10-16
I really need to know how to install a file. I downloaded Deluge, and it's a tar.gz file. I extracted it and no .exe or whatever. I really need to know how to install files on linux. Please :)

---

### Post by bodhi.zazen on 2007-10-16
Look up ^^ It's a sticky

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by Pumalite on 2007-10-16
Delete

---

### Post by tarchy on 2007-10-16
> **bodhi.zazen said:**
> Look up ^^ It's a sticky

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

Well the install file is on my Desktop, I can't see where I should put it to use this command:

```
sudo aptitude install deluge.0.5.5
```

---

### Post by tarchy on 2007-10-16
I have read the sticky and it does not help me.

I try installing the file, but it says it's not found. So where do I put it or what do I do..?

---

### Post by Codix121 on 2007-10-16
this:

```

sudo aptitude install deluge.0.5.5

```

goes in your terminal
go to:

APPLICATIONS > ACCESSORIES > TERMINAL

**EDIT**

if you cannot find it try using

SYNAPTIC 

And look for deluge.

---

### Post by tarchy on 2007-10-16
> Couldn't find any package whose name or description matched "deluge.0.5.5"
No packages will be installed, upgraded, or removed.


What is Synaptic?

---

### Post by Sayers on 2007-10-16
A package management tool, seriously, Codix121 just spoon fed you the answer

---

### Post by tarchy on 2007-10-16
Ok Synaptic does not have Deluge. I really need to know how to install this...grrr :(

---

### Post by tarchy on 2007-10-16
> Couldn't find any package whose name or description matched "deluge.0.5.5"
No packages will be installed, upgraded, or removed.

Did you not see this? I tried that command. This came up. Synaptic did NOT have deluge.

---

### Post by Codix121 on 2007-10-16
Go here;

[http://packages.debian.org/sid/deluge-torrent/ia64/download](http://packages.debian.org/sid/deluge-torrent/ia64/download)

and downloaded the .DEB

this should be easy because a DEB works just like a .exe
it'll walk you throw the install process.

---

### Post by bodhi.zazen on 2007-10-16
> **tarchy said:**
> I have read the sticky and it does not help me.

I try installing the file, but it says it's not found. So where do I put it or what do I do..?

Oh, sorry.

You have two options.

The first, and IMO best is to use one of the programs to install from the repositories.

You may need to enable your repositories : [Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)


1. Open a terminal. 

sudo apt-get install deluge
sudo aptitude install deluge

2. Synaptic

System -> Administration -> Synaptic Package manager

Search for deluge

3. use Add/Remove

Go under applications -> Add/Remove

put deluge in the search box

===============

Or you can install from source.

1. Right click on the deluge tar and extract it. Read the Read me

Likely 

```
cd ~/Desktop/deluge*

sudo apt-get install build-essential

./configure
make
make install
```

---

### Post by bodhi.zazen on 2007-10-16
> **Codix121 said:**
> Go here;

[http://packages.debian.org/sid/deluge-torrent/ia64/download](http://packages.debian.org/sid/deluge-torrent/ia64/download)

and downloaded the .DEB

this should be easy because a DEB works just like a .exe
it'll walk you throw the install process.

No, a .deb is not like an .exe :lolflag:

---

### Post by vambo on 2007-10-16
> **tarchy said:**
> Did you not see this? I tried that command. This came up. Synaptic did NOT have deluge.

Suppose you didn't see this then ;)

> A Bittorrent client written in Python/PyGTK
Deluge is a Bittorrent client, created using Python and GTK+.

Deluge is intended to bring a native, full-featured client to Linux GTK
desktop environments such as Gnome and XFCE.

It uses Rasterbar's version of libtorrent, and python bindings written
by Kripkenstein.

 Homepage: [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)


The package description from Synaptic

---

### Post by Codix121 on 2007-10-16
it is in the fact that it takes you to Package installer.
and all you do is click next.

maybe not "technically" like a .exe
but it installs easily.

---

### Post by bodhi.zazen on 2007-10-16
> **vambo said:**
> Suppose you didn't see this then ;)

...

The package description from Synaptic

Be nice , deluge is in universe he likely needs to enable the repository

See my link on enabling repos ;)

---

### Post by vambo on 2007-10-16
oooops :oops:

---

### Post by bodhi.zazen on 2007-10-16
> **Codix121 said:**
> it is in the fact that it takes you to Package installer.
and all you do is click next.

maybe not "technically" like a .exe
but it installs easily.

Talk about comparing apples to oranges :popcorn:

an .exe is a windows binary and does not run on Linux, without wine or a compatibility layer.

a .deb is an archive and not a binary. .deb does not run on windows.

The similarity is in the gui appearance of an installer, but that is where it ends.

---

### Post by danny joe ritchie on 2007-10-16
Here is a link that might help you out if you ever have to do anything like this in the future [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Codix121 on 2007-10-16
that's what i just said...

Not "technically"
but it is so in the fact that they have installers.
Geez. Ok that's all this post is done.
He should figure it out from here.

---

### Post by tarchy on 2007-10-16
I still can't do it :( That guide you linked me to about enabling repositories is either out of date or I got the wrong version of Linux. I have no idea what I'm doing. Rawr.

When I try this:


1. Open a terminal.

sudo apt-get install deluge
sudo aptitude install deluge

It says the same thing as before (the file isn't there). The package name is this..

deluge-0.5.5.tar.gz - It is located on my Desktop.

---

### Post by tarchy on 2007-10-16
OK I tried installing from source...another error..

It works up to the ./configure.

[IMG]http://img471.imageshack.us/img471/7633/screenshot1oq8.png[/IMG]

---

### Post by tarchy on 2007-10-16
I've changed the server in Software Sources to "Main Sever". See if this helps..

---

### Post by bodhi.zazen on 2007-10-16
If you are going to install from source you will need to install the dependencies first.

You should start with the README

If that fails, check the home page.

---

### Post by danny joe ritchie on 2007-10-16
while you're there (software sources) enable the universe repository!

---

### Post by qpieus on 2007-10-16
I downloaded the deluge tar.gz file. Inside it is a README file. It says ```
==========================
 Deluge BitTorrent Client
==========================

Authors:
	Zach Tibbitts, aka zachtib
	Alon Zakai, aka kripkenstein
	Marcos Pinto, aka markybob
	Andrew Resch, aka andar
	Alex Dedul, aka plisk

Homepage: [http://deluge-torrent.org](http://deluge-torrent.org)

==========================
Contact/Support:
==========================

We have two options available for support:

	Our Forum, at [http://forum.deluge-torrent.org](http://forum.deluge-torrent.org)
		or
	Our IRC Channel, at #deluge on Freenode

==========================
Installation Instructions:
==========================

First, make sure you have the proper build dependencies installed.  On a normal 
Debian or Ubuntu system, those dependencies are:

g++
make
python-all-dev
python-all version >= 2.4
python-dbus
python-gtk2 version >= 2.9
python-xdg
python-support
libboost-dev >= 1.33.1
libboost-thread-dev
libboost-date-time-dev
libboost-filesystem-dev
libboost-serialization-dev
libssl-dev
zlib1g-dev

But the names of the packages may vary depending on your OS / distro.

Once you have the needed libraries installed, build Deluge by running:

	$ make

You shouldn't get any errors.  Then run, as root (or by using sudo): 

	$ make install

and Deluge will be installed.  By default, Deluge will be installed to the
prefix /usr.  If you wish, you can install Deluge to a different prefix by
specifying it when you install it:

	$ PREFIX=yourprefixhere make install

So, to install to /usr/local, run:

	$ PREFIX=/usr/local make install

You can then run Deluge by executing:

	$ deluge
```

So you are getting the error with ./configure because there is no configure file. Follow the directions from the readme.

run```
make
``` followed by```
make install
```
the run deluge by typing deluge in a terminal. You could also set up a launcher so you can load it via an icon or menu item.

Before you do any of this though, make sure you have build-essential installed```
sudo apt-get install build-essential
```

---

### Post by tarchy on 2007-10-16
sudo apt-get install build-essential =

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by tarchy on 2007-10-16
Thanks a lot for the help guys and gals if any :P I am too much of a noob to do this, so I'm just installing Azueras which I can actually find on Synaptic :P. Thanks again.

---

### Post by lisati on 2007-10-16
> **bodhi.zazen said:**
> No, a .deb is not like an .exe :lolflag:

True....but it can still walk you through the installation.

---

### Post by qpieus on 2007-10-16
> **tarchy said:**
> sudo apt-get install build-essential =

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Did you have synaptic open at the time you ran sudo apt-get install build-essential  ? The error you got can be caused by synaptic being open at the same time. I may have seen this error a few times :)

---

