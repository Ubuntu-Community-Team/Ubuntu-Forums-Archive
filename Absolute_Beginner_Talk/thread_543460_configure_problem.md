---
title: "configure problem"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ponch on 2007-09-05
Hi everyone,

Let me start by saying that I am new to linux so please bear with me.  I'll do my best to keep up. **:**o)

I'm trying to install gnucash 2.0.5 and configure fails with the following message:

checking for GLIB - version >= 2.4.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.0, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB >= 2.4 is required to build Gnucash; please make sure you have the
*** development headers installed. The latest version of GLIB is
*** always available at [ftp://ftp.gnome.org/pub/gnome/sources/glib/](ftp://ftp.gnome.org/pub/gnome/sources/glib/).


Now here comes the dumb question:  How do I either set the LD_LIBRARY_PATH,  PKG_CONFIG_PATH, or locate the offending glib 2.10.3 to delete it?  And which of the three would be the most appropriate method of fixing the error?

I'm running Dapper on a System 76 Gazelle Performance Laptop with Intel Centrino Duo  2Ghz processor, 2gig ram, and a 100gig HD.

Any help will be very much appreciated as I've spent the last couple of weeks googling and searching the forum for similar problems with no avail.

TIA

Tom

---

### Post by RomeReactor on 2007-09-05
Hi. Is there a particular reason you need to compile gnucash, other than to get the newest version? it's in Dapper's repositories, as far as I know. Otherwise you can get .deb packages from [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnucash&searchon=names&subword=1&version=dapper&release=all"). 

Not to discourage you from compiling, but you'd have an easier time just installing from the repositories. Just enable the universe repositories from Synaptic (System->Administration->Synaptic Package Manager); in Synaptic go to Settings->Repositories. One of the tabs there will allow you to enable them. Once the checkboxes for the repositories are marked, press the **Reload** button in Synaptic, search for gnucash, and install.

---

### Post by ponch on 2007-09-05
Thanks for the reply.

 Yes, I am trying to install the latest version of gnucash.  Although I had the same thing happen when trying to install the latest version gpsim.  At this point it seems that anything that requires a check for glib 2.4 or greater gives me the same problem.

As far as I can tell that still leaves me with a mismatch of versions and I just can't figure out how to correct it.

Thanks again for any help.

Tom

---

