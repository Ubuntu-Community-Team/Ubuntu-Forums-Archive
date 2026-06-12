---
title: "gtk gnutella, working deb?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2007-02-08
So my gtk gnutella is due to "become old" soon and I've had quite the adventure trying to find a .deb for the latest version that works. Can someone suggest one? If not can someone suggest another good /tella application that can be installed with ease?

---

### Post by dave37 on 2007-02-09
This worked for me, download the platform independant source from the GTK Gnutella website and from their readme:

Supplementary Compile Instructions for Debian-based Systems
	===========================================================

Unfortunately, many people have trouble compiling Gtk-Gnutella on Linux
distributions albeit it should be very simple. The following applies to
Debian-based system that is also Ubuntu.


1. Dependencies:
================

You'll have to install the following packages:

apt-get install gcc		# GCC; any version is fine
apt-get install make		# the make tool; any version is fine
apt-get install zlib1g-dev	# zlib
apt-get install libxml2-dev	# libxml 2.x
apt-get install libgnutls-dev	# GNU TLS

For the Gtk+ 2.x front-end you'll need these:

apt-get install libglib2.0-dev	# GLib 2.x
apt-get install libgtk2.0-dev	# Gtk+ 2.x

If you want to use the Gtk+ 1.2 front-end instead:

apt-get install libglib1.2-dev	# GLib 1.2
apt-get install libgtk1.2-dev	# Gtk+ 1.2

The following packages are optional:

apt-get install libsqlite3-dev 	# SQLite 3.x
apt-get install libdbus-1-dev	# D-Bus


2. Build:
=========

Run from the top of the source tree:

  $ fakeroot debian/rules binary

and it will build the .deb package for you in the parent directory.


3. Finish:
==========

You can then run Gtk-Gnutella without installing:

 $ src/gtk-gnutella

To install Gtk-Gnutella just run (version and architecture will vary):

 $ cd ..
 $ su
 # dpkg --install gtk-gnutella_0.96.3-0_i386.deb

For further compile options and instructions, see the README file and
edit the debian/rules file to change the line calling "Configure" to suit
your taste.

$Id: README.Debian 12207 2006-11-03 22:05:36Z rmanfredi $

---

### Post by DrMilo on 2007-02-09
I get to build and get:

bash: $: command not found

I thought it was the "$" so I cut it off and got:

bash: fakeroot: command not found

So I installed fakeroot through synaptic and got:

/usr/bin/fakeroot: line 150: debian/rules: No such file or directory

So I said, well it's in a different path so:

/usr/bin/fakeroot: line 150: /gtk-gnutella-0.96.3/debian/rules: No such file or directory

I'm stuck.

---

### Post by dave37 on 2007-02-10
I'm of no help with that unfortunately, but I did find this link in another thread, it's a .deb package of it:

[http://www.box.net/public/tkrq1m83j0](http://www.box.net/public/tkrq1m83j0)

---

### Post by DrMilo on 2007-02-10
> **dave37 said:**
> I'm of no help with that unfortunately, but I did find this link in another thread, it's a .deb package of it:



[http://www.box.net/public/tkrq1m83j0](http://www.box.net/public/tkrq1m83j0)

I'm afraid I've tried that one already. Gets a dependency error. 

libatk1.0.0

---

### Post by Marsolin on 2007-02-10
I'm not sure that I understand the problem. All of the Ubuntu versions have [Gtk-Gnutella]("http://linuxappfinder.com/package/gtk-gnutella") in the repos.  Have you tried the version from Feisty?

---

### Post by DrMilo on 2007-02-10
> **Marsolin said:**
> I'm not sure that I understand the problem. All of the Ubuntu versions have [Gtk-Gnutella]("http://linuxappfinder.com/package/gtk-gnutella") in the repos.  Have you tried the version from Feisty?

When I try the Feisty version I get the same dependency error. 

0.96.1 is the latest version Ubuntu has released, it is due to become obsolete. Even if it wasn't I'm getting problems with either installing or running everything I've tried. I've never had this many issues with finding a .deb that I wanted before.

---

### Post by Marsolin on 2007-02-10
I've never tried it, but I heard that there is somewhere that you can request a backport for Ubuntu.

---

### Post by DrMilo on 2007-02-11
> **Marsolin said:**
> I've never tried it, but I heard that there is somewhere that you can request a backport for Ubuntu.

All that seems to do is give me error messages.

---

