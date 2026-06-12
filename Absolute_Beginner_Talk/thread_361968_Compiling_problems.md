---
title: "Compiling problems"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2007-02-15
Hei all!

Im having some problems compling programs. this has happened several times, and I ve looked aroung on the forum for an answer but no joy. So heres the specific problem Im having now. Im trying to compile [Ubuntu home backup](https://wiki.ubuntu.com/UbuntuHomeBackup). When I go to run the command 

```
./configure
```

I get an error message like:
```

jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
```

However install-sh is in the directory:

```
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ dir
aclocal.m4      config.status  Makefile.am    stamp-h1
AUTHORS         configure      Makefile.in    stamp-h.in
autogen.sh      configure.in   missing        ubuntu-home-backup-0.2.glade
autom4te.cache  COPYING        mkinstalldirs  ubuntu-home-backup-0.2.glade.bak
ChangeLog       depcomp        NEWS           ubuntu-home-backup-0.2.gladep
config.h        INSTALL        po             ubuntu-home-backup-0.2.gladep.bak
config.h.in     install-sh     README
config.log      Makefile       src
```

I have also already done this:

```
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So what do I do? am I missing something? It has happened with another program as well, I jst cant quite figure it out. Please help!!!

---

### Post by sardion on 2007-02-15
Try

chmod a+x install-sh

that will mark it as executable.  sometimes permissions get screwed up when zipping or tarring happens.

---

### Post by Jussi01 on 2007-02-15
Still no go...

```
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ chmod a+x install-sh
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
```

---

### Post by sardion on 2007-02-15
Hmmmm.... (taking a shot in the dark now)

sudo aptitude install autotools-dev

---

### Post by Jussi01 on 2007-02-15
hmmm.. maybe we will have to aim better :D ;) ...

```
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ sudo aptitude install autotools-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  autotools-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.1kB of archives. After unpacking 168kB will be used.
Writing extended state information... Done
Get:1 http://fi.archive.ubuntu.com edgy/main autotools-dev 20060223.1 [60.1kB]
Fetched 60.1kB in 0s (429kB/s)     
Selecting previously deselected package autotools-dev.
(Reading database ... 162520 files and directories currently installed.)
Unpacking autotools-dev (from .../autotools-dev_20060223.1_all.deb) ...
Setting up autotools-dev (20060223.1) ...
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
```

I am at a loss here, no idea what to do.

---

### Post by sardion on 2007-02-15
If you don't consider what you are working with private ... can you attach a tar or zip file of that directory and let me try it on my machine?

I am also at a loss now and I have been a *nix user and developer for a long time.

---

### Post by Jussi01 on 2007-02-15
No, its not private - you can download the package from the link in the first post. Thanks a million for the help so far. :D

---

### Post by sardion on 2007-02-15
OK... that's a weird one.  Do this:

sudo aptitude install automake1.9


Basically, the code you downloaded is made to work with a specific version of automake (version 1.9) while 1.10 is the default with edgy.  Maybe you should let the author know...

If you run into this with other things, the way I figured it out was to do

ls -lh

and got:

lrwxrwxrwx 1 d d   31 2007-02-14 22:51 INSTALL -> /usr/share/automake-1.9/INSTALL
lrwxrwxrwx 1 d d   34 2007-02-14 22:51 install-sh -> /usr/share/automake-1.9/install-sh

which means that install-sh was a symlink (like a file alias) to /usr/share/automake-1.9/install-sh which does not exist since automake-1.9 was not instaleld.

Glad to help

---

### Post by Jussi01 on 2007-02-15
Thanks a million - works like a charm now!! See, this is one reason I reccomend all of my mates to get ubuntu - the support is second to none. thanks again!

---

### Post by Jussi01 on 2007-02-15
You know, If we had bothered to read that page, there is a note - the last 2 lines of text - that says just that... oops...

---

### Post by sardion on 2007-02-15
Actually I just posed those last two lines.

---

### Post by Jussi01 on 2007-02-15
Ok, we have a new problem. 

```
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ make
make  all-recursive
make[1]: Entering directory `/home/jussi/ubuntu-home-backup-0.1'
Making all in src
make[2]: Entering directory `/home/jussi/ubuntu-home-backup-0.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -I/usr/local/include/cairo -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -I/usr/local/include/cairo -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT support.o -MD -MP -MF ".deps/support.Tpo" -c -o support.o support.c; \
        then mv -f ".deps/support.Tpo" ".deps/support.Po"; else rm -f ".deps/support.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -I/usr/local/include/cairo -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT interface.o -MD -MP -MF ".deps/interface.Tpo" -c -o interface.o interface.c; \
        then mv -f ".deps/interface.Tpo" ".deps/interface.Po"; else rm -f ".deps/interface.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -I/usr/local/include/cairo -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
        then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:208: error: conflicting types for 'get_radiobutton_choice_page0'
callbacks.c:193: error: previous implicit declaration of 'get_radiobutton_choice_page0' was here
callbacks.c:235: error: conflicting types for 'get_radiobutton_choice_for_navigating_page2'
callbacks.c:105: error: previous implicit declaration of 'get_radiobutton_choice_for_navigating_page2' was here
callbacks.c:258: error: conflicting types for 'get_radiobutton_choice_for_navigating_page6_back'
callbacks.c:167: error: previous implicit declaration of 'get_radiobutton_choice_for_navigating_page6_back' was here
callbacks.c:281: error: conflicting types for 'get_radiobutton_choice_page1'
callbacks.c:194: error: previous implicit declaration of 'get_radiobutton_choice_page1' was here
callbacks.c:312: error: conflicting types for 'get_radiobutton_choice_for_navigating_page1'
callbacks.c:89: error: previous implicit declaration of 'get_radiobutton_choice_for_navigating_page1' was here
callbacks.c:348: error: conflicting types for 'get_radiobutton_choice_for_navigating_page2_back'
callbacks.c:97: error: previous implicit declaration of 'get_radiobutton_choice_for_navigating_page2_back' was here
callbacks.c:384: error: conflicting types for 'get_backup_entry_name_page2'
callbacks.c:195: error: previous implicit declaration of 'get_backup_entry_name_page2' was here
callbacks.c: In function `get_backup_entry_name_page2':
callbacks.c:385: warning: assignment discards qualifiers from pointer target type
callbacks.c: At top level:
callbacks.c:391: error: conflicting types for 'get_email_entry_address_page3'
callbacks.c:198: error: previous implicit declaration of 'get_email_entry_address_page3' was here
callbacks.c: In function `get_email_entry_address_page3':
callbacks.c:395: warning: assignment discards qualifiers from pointer target type
callbacks.c: At top level:
callbacks.c:404: error: conflicting types for 'get_ftp_server_entry_page4'
callbacks.c:199: error: previous implicit declaration of 'get_ftp_server_entry_page4' was here
callbacks.c: In function `get_ftp_server_entry_page4':
callbacks.c:405: warning: assignment discards qualifiers from pointer target type
callbacks.c:406: warning: assignment discards qualifiers from pointer target type
callbacks.c:407: warning: assignment discards qualifiers from pointer target type
callbacks.c: At top level:
callbacks.c:433: error: conflicting types for 'get_checkbox_choice_page6'
callbacks.c:196: error: previous implicit declaration of 'get_checkbox_choice_page6' was here
callbacks.c:452: error: conflicting types for 'get_checkbox_choice_page5'
callbacks.c:201: error: previous implicit declaration of 'get_checkbox_choice_page5' was here
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/jussi/ubuntu-home-backup-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jussi/ubuntu-home-backup-0.1'
make: *** [all] Error 2
```

the configure went fine, but the make has a whole lot of errors. am I missing something else or is the program screwed?

---

### Post by Jussi01 on 2007-02-15
> **sardion said:**
> Actually I just posed those last two lines.

Aha...:D

---

### Post by sardion on 2007-02-15
Hmm... compiled fine for me.
Try:

sudo aptitude install libgtk2.0-dev

and then do it again.

---

### Post by sardion on 2007-02-15
I hate to give up on things but you could also try

sudo aptitude install hubackup

and use that.  I don't, but people recommend it.

---

### Post by Jussi01 on 2007-02-15
No go again. 

```
jussi@jussi-laptop:~/ubuntu-home-backup-0.1$ sudo aptitude install libgtk2.0-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

Then "make" gives the same errors back to me.

---

### Post by Jussi01 on 2007-02-15
> **sardion said:**
> I hate to give up on things but you could also try

sudo aptitude install hubackup

and use that.  I don't, but people recommend it.

Heheh, yeah, I hear where your coming from, Problem is I want other things to be able to be compiled as well, so I kind of want to fix the problem. otherwise - brilliant idea.

---

### Post by sardion on 2007-02-15
Attached are the compiled versions from my system.  Try running them.?

---

### Post by sardion on 2007-02-15
I think this package is essentialyl broken on edgy.  Compiling only seems to work on feisty (which I am running).

---

### Post by Jussi01 on 2007-02-15
Ok, well thanks a lot. It works no problems. Once again, I appreciate all your help.

---

