---
title: "new version of Gtk-Gnutella"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-01-07
Hi,

Could you guide me how I can install the new version of Gtk-Gnutella (gtk-gnutella-0.96.3)?
I've downloaded the *.tar.bz2 file but I can't install it.

Thanks,

---

### Post by taurus on 2007-01-07
Look at Section 4 of this guide.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by linux-beginner on 2007-01-07
I've had all tried. If I type 
./configure

I get this message> bash: ./configure: No such file or directory

:confused:

---

### Post by taurus on 2007-01-07
Have you unpacked it first?  What's the output of this command from a terminal then?

```
ls -la ~/Desktop
```

---

### Post by linux-beginner on 2007-01-07
I've opened it in an other folder.
That folders contains: 
> total 744
drwxr-xr-x 11 mehdi mehdi   4096 2006-11-10 00:01 .
drwxr-xr-x  5 mehdi mehdi   4096 2007-01-07 17:02 ..
-rw-r--r--  1 mehdi mehdi   3866 2006-11-10 00:01 AUTHORS
-rw-r--r--  1 mehdi mehdi 345265 2006-11-10 00:01 ChangeLog
-rw-r--r--  1 mehdi mehdi  20794 2006-11-10 00:01 config_h.SH
-rw-r--r--  1 mehdi mehdi   6929 2006-11-10 00:01 config.sh.xmingw
-rwxr-xr-x  1 mehdi mehdi 189035 2006-11-10 00:01 Configure
-rwxr-xr-x  1 mehdi mehdi   3016 2006-11-10 00:01 configure.gnu
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 cygwin
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 debian
drwxr-xr-x  7 mehdi mehdi   4096 2006-11-10 00:01 doc
drwxr-xr-x  5 mehdi mehdi   4096 2006-11-10 00:01 extra_files
-rw-r--r--  1 mehdi mehdi   3334 2006-11-10 00:01 GEO_LICENSE
-rwxr-xr-x  1 mehdi mehdi   5616 2006-11-10 00:01 gtk-gnutella_spec.SH
-rwxr-xr-x  1 mehdi mehdi   4461 2006-11-10 00:01 install.SH
-rw-r--r--  1 mehdi mehdi   1278 2006-11-10 00:01 Jmakefile
-rw-r--r--  1 mehdi mehdi  15145 2006-11-10 00:01 LICENSE
-rw-r--r--  1 mehdi mehdi   5385 2006-11-10 00:01 Makefile.SH
-rw-r--r--  1 mehdi mehdi  14873 2006-11-10 00:01 MANIFEST
-rw-r--r--  1 mehdi mehdi  25755 2006-11-10 00:01 MPL-1.1.txt
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 pixmaps
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 po
-rw-r--r--  1 mehdi mehdi  14010 2006-11-10 00:01 README
-rw-r--r--  1 mehdi mehdi   1616 2006-11-10 00:01 README.Debian
-rw-r--r--  1 mehdi mehdi   5112 2006-11-10 00:01 README.xmingw
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 scripts
drwxr-xr-x  7 mehdi mehdi   4096 2006-11-10 00:03 src
-rw-r--r--  1 mehdi mehdi    681 2006-11-10 00:01 TODO
drwxr-xr-x  6 mehdi mehdi   4096 2006-11-10 00:01 U


---

### Post by taurus on 2007-01-07
Try running your comand again except now using capital C instead.

```
./Configure
```

---

### Post by linux-beginner on 2007-01-07
yea, you are right. I've done it. But now the command "make" gives this:
> make: *** No targets specified and no makefile found.  Stop.
:-k

---

### Post by taurus on 2007-01-07
Try to install it with

```
./install.SH
(and if it complains about permission, then insert the sudo in front of it.)
sudo ./install.SH
```

---

### Post by linux-beginner on 2007-01-07
By typing "./install.SH" or "sudo ./install.SH" I get:
> Can't find config.sh.


---

### Post by Hendrixski on 2007-01-07
gtk gnutella is a pretty good program.  I forgot how I installed it,but every once in a while they make a release that is no longer backwards compatible and you have to upload the latest version if you want it to keep working smoothly.

Generally to install a program from a tarball, when you download it with Firefox you have the option of opening it with archive manager, or some other tool that will allow you to extract it, so that you don't have to extract it fromthe command line later, THen look for something with a .sh at the end, that's a script file.  running it isusually what you need to install... unless the directions tell you otherwise.

>  -rwxr-xr-x 1 mehdi mehdi 4461 2006-11-10 00:01 install.SH  looks like the right one, make sure you are in the right directory when you run it.

---

### Post by taurus on 2007-01-07
What's the output of this command again?

```
ls -la
```
Otherwise, give me the site where you've downloaded it and I will have a look on my computer to see what's going on.  And by the way, I assume you know that there is a copy of gtk-gnutella in the repos!

---

### Post by linux-beginner on 2007-01-07
The output:
> total 744
drwxr-xr-x 11 mehdi mehdi   4096 2006-11-10 00:01 .
drwxr-xr-x  4 mehdi mehdi   4096 2007-01-07 17:44 ..
-rw-r--r--  1 mehdi mehdi   3866 2006-11-10 00:01 AUTHORS
-rw-r--r--  1 mehdi mehdi 345265 2006-11-10 00:01 ChangeLog
-rw-r--r--  1 mehdi mehdi  20794 2006-11-10 00:01 config_h.SH
-rw-r--r--  1 mehdi mehdi   6929 2006-11-10 00:01 config.sh.xmingw
-rwxr-xr-x  1 mehdi mehdi 189035 2006-11-10 00:01 Configure
-rwxr-xr-x  1 mehdi mehdi   3016 2006-11-10 00:01 configure.gnu
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 cygwin
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 debian
drwxr-xr-x  7 mehdi mehdi   4096 2006-11-10 00:01 doc
drwxr-xr-x  5 mehdi mehdi   4096 2006-11-10 00:01 extra_files
-rw-r--r--  1 mehdi mehdi   3334 2006-11-10 00:01 GEO_LICENSE
-rwxr-xr-x  1 mehdi mehdi   5616 2006-11-10 00:01 gtk-gnutella_spec.SH
-rwxr-xr-x  1 mehdi mehdi   4461 2006-11-10 00:01 install.SH
-rw-r--r--  1 mehdi mehdi   1278 2006-11-10 00:01 Jmakefile
-rw-r--r--  1 mehdi mehdi  15145 2006-11-10 00:01 LICENSE
-rw-r--r--  1 mehdi mehdi   5385 2006-11-10 00:01 Makefile.SH
-rw-r--r--  1 mehdi mehdi  14873 2006-11-10 00:01 MANIFEST
-rw-r--r--  1 mehdi mehdi  25755 2006-11-10 00:01 MPL-1.1.txt
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 pixmaps
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 po
-rw-r--r--  1 mehdi mehdi  14010 2006-11-10 00:01 README
-rw-r--r--  1 mehdi mehdi   1616 2006-11-10 00:01 README.Debian
-rw-r--r--  1 mehdi mehdi   5112 2006-11-10 00:01 README.xmingw
drwxr-xr-x  2 mehdi mehdi   4096 2006-11-10 00:01 scripts
drwxr-xr-x  7 mehdi mehdi   4096 2006-11-10 00:03 src
-rw-r--r--  1 mehdi mehdi    681 2006-11-10 00:01 TODO
drwxr-xr-x  6 mehdi mehdi   4096 2006-11-10 00:01 U


and the address of the site: 
[http://sourceforge.net/project/showfiles.php?group_id=4467](http://sourceforge.net/project/showfiles.php?group_id=4467)
:-#

---

### Post by taurus on 2007-01-07
Okay, I think I know what's your problem is.  When you run ./Configure, it asks you a bunch of questions.  Do you get any error message that the end?  Why don't you paste the last screen of text from that command?

---

### Post by linux-beginner on 2007-01-07
yea,
These are the error messages:
> ERROR: Cannot compile against GLib.
ERROR: Cannot compile against Gtk+.


---

### Post by linux-beginner on 2007-01-07
The last screen of the command ./Configure is:
> Checking whether we can use sendfile() with large file support...
It looks like we can use sendfile().
 
Checking whether -mieee should be used...
 
End of configuration questions.

Feature Summary (Version 0.96.3):
-------------------------------------------------
GLib version                       : glib-1.x
GUI front-end                      : GTK1
GNU TLS support                    : yes
IPv6 support                       : yes
NLS (Native Language Support)      : yes
Fast assertions                    : yes
DBus support (experimental)        : yes
SQLite (experimental)              : yes
Remote Shell Interface (deprecated): yes
-------------------------------------------------
ERROR: Cannot compile against GLib.
ERROR: Cannot compile against Gtk+.


During the running of ./Configure I got this question:
> Which compiler compiler (yacc) shall I use?
I answered "gcc"
Is this a good compiler?
W

---

### Post by taurus on 2007-01-07
Since there is a problem from running ./Configure, you cannot run the next command, make, until you fix it.  I think you have to install the development packages for glib and gtk+ if you want to build it from source.  Otherwise, install it with synaptic/apt-get/aptitude.  The version in the repo is 0.96.1 so it's not that old.

```
sudo aptitude update
sudo aptitude install gtk-gnutella
```

---

### Post by linux-beginner on 2007-01-07
Thanks for all information!:p

---

### Post by deadlydeathcone on 2007-01-10
I made good (not checkinstall) [deb of v 0.96.3]("http://www.box.net/public/tkrq1m83j0"). If you'd like to know how to package it yourself let me know and I can help you out.

---

