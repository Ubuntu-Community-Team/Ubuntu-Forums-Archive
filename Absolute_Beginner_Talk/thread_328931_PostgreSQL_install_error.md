---
title: "PostgreSQL install error"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2006-12-31
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

### Post by x1a4 on 2007-01-09
Fixed it.  The problem was a blank line in the first stanza of /etc/debconf.conf

---

### Post by borland-c on 2007-01-21
I have problem with installing too
here is enf of log of install
```

checking for library containing setproctitle... no
checking for library containing dlopen... -ldl
checking for library containing socket... none required
checking for library containing shl_load... no
checking for library containing getopt_long... none required
checking for library containing crypt... -lcrypt
checking for library containing fdatasync... none required
checking for library containing shmget... none required
checking for -lreadline... no
checking for -ledit... no
configure: error: readline library not found

```I try to install version 8.2.1
as far as I understand not found functions -lreadline and -ledit
how I can get it?

---

### Post by x1a4 on 2007-01-23
> **borland-c said:**
> I have problem with installing too
<snip>
checking for -lreadline... no
checking for -ledit... no
configure: error: readline library not found
[/code]I try to install version 8.2.1
as far as I understand not found functions -lreadline and -ledit
how I can get it?

Using Synaptic, search for *readline* and *ledit* in the package name, select the appropriate packages and click the 'Apply' button.  Or you can do it from a terminal.

```
sudo apt-get install ledit libreadline5 readline-common
```

---

### Post by garbergs on 2007-01-26
How do you go from knowing that you need the readline library to getting the correct library names for apt-get?

Trying "apt-get install readline" results in "could not find package", so how do you find out it's called "libreadline5"? Btw, my apt-get cannot find "readline-common".

[EDIT]

I solved my readline-problem thanks to this thread:  [http://www.ubuntuforums.org/showthread.php?t=58075](http://www.ubuntuforums.org/showthread.php?t=58075)  using the command:

apt-get install libreadline5-dev

After "./configure" I tried "make", which resulted in:

y.tab.c: In function &#8216;base_yyparse&#8217;:
y.tab.c:12189: internal compiler error: Segmentation fault

So then I used Synaptic Package Manager to find out there was a package named "postgresql-8.0". I typed:
apt-get install postgresql-8.0

and that worked! The PostgreSQL server is running, not version 8.1.2, but 8.0 will do.

[EDIT]
I found out that you can search for packages by typing:

apt-get cache readline

where "readline" is a part of the package name you're looking for.

---

### Post by x1a4 on 2007-01-26
Hi,

If you can't install a package using Synaptic or apt-get it means you have a repository missing from your */etc/apt/sources.list* file.  Use Synaptic to include ALL repositories or edit sources.list by hand.  Mine contains these entries:  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse universe main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted

---

