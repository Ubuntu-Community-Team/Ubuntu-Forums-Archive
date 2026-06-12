---
title: "(Repost) Can't install PostgreSQL 8.1 on Edgy"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-01-03
Hi,

I'm having trouble installing PostgreSQL on XUbuntu 6.10 (Edgy Eft).

I tried to install using Synaptic and received an error stating the pre-installation script in postgresql-common_62_all.deb returned exit code 9. Then I tried to run

sudo apt-get -f install

and got the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
gnome-bin libwxgtk2.6-0 libgnome32 gnome-libs-data libart2 libgnorbagtk0 gdk-imlib1 dcraw libwxbase2.6-0 libgnomeui32 libdb3
libcrypto++5.2c2a imlib-base liborbit0 gdk-imlib11 libgnomesupport0 libzvt2 liballegro4.2 libgnorba27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
postgresql-common
The following NEW packages will be installed:
postgresql-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/94.8kB of archives.
After unpacking, 442kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
driver type not specified (perhaps you need to re-read debconf.conf(5)) at /usr/share/perl5/Debconf/Db.pm line 35, <DEBCONF_CONFIG> chunk 3.
(Reading database ... 208653 files and directories currently installed.)
Unpacking postgresql-common (from .../postgresql-common_62_all.deb) ...
debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
driver type not specified (perhaps you need to re-read debconf.conf(5)) at /usr/share/perl5/Debconf/Db.pm line 35, <DEBCONF_CONFIG> chunk 3.
dpkg: error processing /var/cache/apt/archives/postgresql-common_62_all.deb (--unpack):
subprocess pre-installation script returned error exit status 9
Errors were encountered while processing:
/var/cache/apt/archives/postgresql-common_62_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Exit 100


Any ideas on how to fix this? Thank you.

---

### Post by Dmole on 2007-01-03
did you make a "/etc/debconf.conf"?

---

### Post by x1a4 on 2007-01-04
> **Dmole said:**
> did you make a "/etc/debconf.conf"?

I didn't make it, but I do have it.  Contents of /etc/debconf.conf are:

Config: configdb
Templates: templatedb

Frontend: Dialog

# World-readable, and accepts everything but passwords.
Name: config
Driver: File
Mode: 644
Reject-Type: password
Filename: /var/cache/debconf/config.dat

# Not world readable (the default), and accepts only passwords.
Name: passwords
Driver: File
Mode: 600
Backup: false
Required: false
Accept-Type: password
Filename: /var/cache/debconf/passwords.dat

# Set up the configdb database. By default, it consists of a stack of two
# databases, one to hold passwords and one for everything else.
Name: configdb
Driver: Stack
Stack: config, passwords

# Set up the templatedb database, which is a single flat text file
# by default.
Name: templatedb
Driver: File
Mode: 644
Filename: /var/cache/debconf/templates.dat

---

### Post by x1a4 on 2007-01-09
> **Dmole said:**
> did you make a "/etc/debconf.conf"?

Fixed it.  The problem was a blank space in the first stanza above Frontend: dialog.

---

