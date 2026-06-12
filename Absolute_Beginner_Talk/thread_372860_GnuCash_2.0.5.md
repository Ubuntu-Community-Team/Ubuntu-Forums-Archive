---
title: "GnuCash 2.0.5"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-02-28
Hi all

I just realised that while I am running GnuCash 2.0.1, GnuCash is now up to 2.0.5

How do I upgrade applications? In particular this one, but also generally how do i go about it

Thanks

Patrick

---

### Post by Mumbo719 on 2007-02-28
Install Gnucash 2.0.5 for Ubuntu Edgy. You will have to build it from scratch. The step by step guide is here.

Works like a charm.

[http://www.linuxmint.com/forum/viewtopic.php?t=1283]("http://www.linuxmint.com/forum/viewtopic.php?t=1283")

---

### Post by ozPATT on 2007-02-28
Hi, do I have to uninstall my old GNU cash? And will it affect my current account files?

Thanks

Patrick

edit: too late! haha, I (think) backed up my account, then started off the new install :) hopefully it isok and doesnt conflict with the other. will let you know how i get on 

thanks for the prompt reply above

---

### Post by ozPATT on 2007-02-28
installation failed apparently :(

---

### Post by Maestro23 on 2007-02-28
> **ozPATT said:**
> installation failed apparently :(

What exactly did you do?

---

### Post by ozPATT on 2007-02-28
i did exactly as the above link told me to do except that I called my folder GnuCash 2.0.5

I renamed to gnucash in case the space was the problem and am tying again, but there are still loads of lines that say something seems to be moved... not sure if that is normal... will see how this one goes

---

### Post by ozPATT on 2007-02-28
failed again :( here is the last bit of checkinstall

```
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-none.png': No such file or directory
 /usr/bin/install -c -m 644 'bar-vplus.png' '/usr/local/share/gnucash/pixmaps/goffice/bar-vplus.png'
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-vplus.png': No such file or directory
 /usr/bin/install -c -m 644 'bar-vminus.png' '/usr/local/share/gnucash/pixmaps/goffice/bar-vminus.png'
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-vminus.png': No such file or directory
 /usr/bin/install -c -m 644 'bar-vboth.png' '/usr/local/share/gnucash/pixmaps/goffice/bar-vboth.png'
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-vboth.png': No such file or directory
 /usr/bin/install -c -m 644 'bar-hplus.png' '/usr/local/share/gnucash/pixmaps/goffice/bar-hplus.png'
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-hplus.png': No such file or directory
 /usr/bin/install -c -m 644 'bar-hminus.png' '/usr/local/share/gnucash/pixmaps/goffice/bar-hminus.png'
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-hminus.png': No such file or directory
 /usr/bin/install -c -m 644 'bar-hboth.png' '/usr/local/share/gnucash/pixmaps/goffice/bar-hboth.png'
/usr/bin/install: setting permissions for `/usr/local/share/gnucash/pixmaps/goffice/bar-hboth.png': No such file or directory
make[5]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/pixmaps'
make[4]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/pixmaps'
Making install in plugins
make[4]: Entering directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/plugins'
Making install in plot_pie
make[5]: Entering directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/plugins/plot_pie'
LC_ALL=C ../../../../intltool-merge -x -u -c ../../../../po/.intltool-merge-cache ../../../../po plugin.xml.in plugin.xml
Found cached translation database
Merging translations into plugin.xml.
CREATED plugin.xml
make[6]: Entering directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/plugins/plot_pie'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnucash/goffice//plugins/plot_pie" || /bin/mkdir -p "/usr/local/lib/gnucash/goffice//plugins/plot_pie"
 /usr/bin/install -c -m 644 'gog-pie-prefs.glade' '/usr/local/lib/gnucash/goffice//plugins/plot_pie/gog-pie-prefs.glade'
/usr/bin/install: setting permissions for `/usr/local/lib/gnucash/goffice//plugins/plot_pie/gog-pie-prefs.glade': No such file or directory
 /usr/bin/install -c -m 644 'gog-ring-prefs.glade' '/usr/local/lib/gnucash/goffice//plugins/plot_pie/gog-ring-prefs.glade'
/usr/bin/install: setting permissions for `/usr/local/lib/gnucash/goffice//plugins/plot_pie/gog-ring-prefs.glade': No such file or directory
 /usr/bin/install -c -m 644 'gog-pie-series.glade' '/usr/local/lib/gnucash/goffice//plugins/plot_pie/gog-pie-series.glade'
/usr/bin/install: setting permissions for `/usr/local/lib/gnucash/goffice//plugins/plot_pie/gog-pie-series.glade': No such file or directory
test -z "/usr/local/lib/gnucash/goffice//plugins/plot_pie" || /bin/mkdir -p "/usr/local/lib/gnucash/goffice//plugins/plot_pie"
 /bin/bash ../../../../libtool --mode=install /usr/bin/install -c  'pie.la' '/usr/local/lib/gnucash/goffice//plugins/plot_pie/pie.la'
libtool: install: warning: relinking `pie.la'
(cd /home/patrick/Personal/Downloads/GnuCash 2.0.5/gnucash-2.0.5/lib/goffice-0.0.4/plugins/plot_pie; /bin/bash ../../../../libtool  --tag=CC --mode=relink gcc -g -O2 -Wall -Wunused -Wmissing-prototypes -Wmissing-declarations -Wdeclaration-after-statement -Wno-pointer-sign -D_FORTIFY_SOURCE=2 -module -avoid-version -no-undefined -o pie.la -rpath /usr/local/lib/gnucash/goffice//plugins/plot_pie gog-pie.lo gog-pie-prefs.lo ../../../../lib/goffice-0.0.4/goffice/libgoffice-1.la -Wl,--export-dynamic -pthread -lglade-2.0 -lgnomeprint-2-2 -lz -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgsf-gnome-1 -lgsf-1 -lbonobo-2 -lgnomevfs-2 -lxml2 -lbonobo-activation -lgconf-2 -lgobject-2.0 -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -lpopt -lm -lm )
../../../../libtool: line 6396: cd: /home/patrick/Personal/Downloads/GnuCash: No such file or directory
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libglade-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnomeui-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libbonoboui-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnome-keyring.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnomecanvas-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnome-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libart_lgpl_2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpangoft2-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libbonobo-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnomevfs-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libxml2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libbonobo-activation.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpopt.la' seems to be moved
gcc -shared  .libs/gog-pie.o .libs/gog-pie-prefs.o  -Wl,--rpath -Wl,/usr/local/lib/gnucash -L/usr/local/lib/gnucash -lgoffice-1 -L/usr/lib -L/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../ -lglade-2.0 -lgnomeprint-2-2 -lz -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lgnomecanvas-2 -lgnome-2 -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgsf-gnome-1 -lgsf-1 -lbonobo-2 -lgnomevfs-2 -lxml2 -lbonobo-activation -lgconf-2 -lgobject-2.0 -lORBit-2 -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -lpopt -lm  -Wl,--export-dynamic -pthread -Wl,-soname -Wl,pie.so -o .libs/pie.so
/usr/bin/install -c .libs/pie.soT /usr/local/lib/gnucash/goffice//plugins/plot_pie/pie.so
/usr/bin/install: setting permissions for `/usr/local/lib/gnucash/goffice//plugins/plot_pie/pie.so': No such file or directory
/usr/bin/install -c .libs/pie.lai /usr/local/lib/gnucash/goffice//plugins/plot_pie/pie.la
/usr/bin/install: cannot stat `.libs/pie.lai': No such file or directory
make[6]: *** [install-goffice_graph_pieLTLIBRARIES] Error 1
make[6]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/plugins/plot_pie'
make[5]: *** [install-am] Error 2
make[5]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/plugins/plot_pie'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4/plugins'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib/goffice-0.0.4'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5/lib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/patrick/Personal/Downloads/gnucash/gnucash-2.0.5'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.
```

I notice though that on all the ones that say "seems to be moved", they refer to i486. My laptop which was a windows laptop would be i386 wouldnt it?

Thanks

Patrick

---

### Post by Mumbo719 on 2007-02-28
No it will not affect your existing working files thay are in a seperate directory. 
If you made the GnuCash 2.0.5 and not just gnucsah  you must do the steps as cd GnuCash 2.0.5 then cd gnucash-2.0.5

When you get to the make command the terminal complains a lot but it works, at least for me and a few others as well.

---

### Post by ozPATT on 2007-03-01
Hi Mumbo, 

I did use the directory name that I had created, not the one in the example, and when I renamed it, I used the new one. But still no joy. I'd like to have it working if possible... Is it much different, given that it is 4 versions above my existing version?

---

### Post by a_lacsa on 2007-03-01
hello,

i am trying to install gnucash for the first time.. I am following the instructions on the link Mumbo gave. however in the first step, when i typed: sudo apt-get build-dep gnucash, I get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_edgy_main_source_Sources - open (2 No such file or directory)

what does that mean?

Thank you in advance...

---

### Post by mazdaracer on 2007-03-03
I guess I did it the hard way, but it did work. Here's my solution:
Via Synaptic, download the following:
build-essentials
libltdl3-dev
libtool
guile-gnome0-glib
libglib2.0-data
libglib2.0-dev
libgconf2-dev
libxml2-dev
libgttk2.0-dev
libgnomeui-dev
libgnomeprint-dev
libgnomeprintui-dev
libgtkhtml3.8-dev

Get the gnuCash source. Do the compile 3 step (configure/make/make install).

Just installed this a couple of hours ago on edgy.

---

### Post by ozPATT on 2007-03-03
Hi mazdaracer, 

I did as you did above - though there were about 2 things i couldnt find in synaptic. During the install process, there were a lot of lines saying "Link Warning: ... seems to be moved" 

However, despite these warnings, now when I load GnuCash, it loads 2.05, so it must have installed ok. Do you know if the warnings mean it is not installed correctly?

Thanks for your help installing this, seems to be working fine so far.

Thanks

Patrick

---

### Post by mike984 on 2007-03-13
If someone can build a package with HBCI or OFX options or supply a repo, Automatix might put in an option for 2.05

[http://www.getautomatix.com/forum/index.php?showtopic=821](http://www.getautomatix.com/forum/index.php?showtopic=821)

---

### Post by mahiyar on 2007-03-18
Mumbo - Thanks for the link. Worked like a charm.

---

### Post by waldorf on 2007-03-23
everything has been working fine for me, but now I am stuck at make. when I type make into the terminal I get 

jn@jn-laptop:~/gnucash/gnucash-2.0.5$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by mahiyar on 2007-03-24
It might mean that the configure has fialed, are you sure you used this "./" before the configure command? try the configure step again, or better still check the download or redownload the file.

---

### Post by waldorf on 2007-03-24
mahiyar-

Thanks for responding to my question. I tried redownloading and it still did not work. Just for the heck of it I also downloaded 2.0.4 and 2.0.3 and tried those. They also got stuck at the make command and gave the same response: make: *** No targets specified and no makefile found.  Stop.

(btw I like your signature line. excellent point.)

---

### Post by mahiyar on 2007-03-24
Did you installed guile-g-wrap? Not installing it might lead to problems as in this thread [http://lists.freebsd.org/pipermail/freebsd-ports/2006-October/036239.html](http://lists.freebsd.org/pipermail/freebsd-ports/2006-October/036239.html)

---

