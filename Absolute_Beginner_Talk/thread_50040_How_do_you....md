---
title: "How do you..."
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-18
...install software that is not included in Synaptic universe ? Such as Firefox 1.0.5 ?
Where does it go once it's downloaded ? And how do you remove software manually ?

Thanks!

---

### Post by cwaldbieser on 2005-07-18
Traditionally, /usr/bin is where most system wide programs end up getting installed.  It is the rough equivalent of "Program Files" on Windows.  However, some programs go in /bin, /sbin, /usr/sbin, /usr/local/bin, etc.  

By convention, most programs that you install from source follow the sequence:
1) Unpack the source tarball.
2) ./configure
3) make
4) sudo make install
If an uninstaller was written, you can run it with "sudo make uninstall".

This can be somewhat messy.  There is a program in the repository called "checkinstall" that will do all those steps for you and create a binary package that will work with the normal install tools (synaptic, apt-get).  This makes uninstalling a lot easier, too.

---

### Post by Nequeo on 2005-07-18
[QUOTE=grofaz]...install software that is not included in Synaptic universe ? Such as Firefox 1.0.5 ?
Where does it go once it's downloaded ? And how do you remove software manually ?

Thanks![/QUOTE]
 Hi,

I'm afraid every Linux program is usually a little different. That can make it very hard to install programs not in Synaptic. I would suggest as a first step to visit this website:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

and follow the steps there. Then click 'reload' in Synaptic, and search for the program you want again. With a little luck, you'll see it.

But to answer your question about Firefox 1.05 directly, here's how you'd do it.

[EDIT]Before we continue, I should mention that the Ubuntu Firefox is actually  version 1.04... But they didn't change the version number! This means you can't install new extensions. However, there is information about how to fix this here (you'll need to scroll down a few posts):
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)
[/EDIT]
The file you download is a .tar.gz file, which is kinda the Linux equivalent of a .zip file. By default, Firefox will save that file to your desktop. Under this assumption, here's how you would install Firefox. 

Open a terminal (right click on the desktop and select 'open terminal') and type the following:

```

$ cd Desktop
$ tar xzvf firefox-1.0.5.installer.tar.gz
[You'll see the files unzipping]
$ cd firefox-installer
$ mkdir ~/apps/firefox1.05
$ ./firefox-installer

```
And then you'll see a graphical Firefox install program. You'll want to change the default install directory though, to the one you created. In this example, *apps/firefox1.05* in your home directory.

The installer will put all the files there. To run the program, you'll want to right click on the panel and select 'Add custom launcher', then browse for the command and locate 'firefox' in the new folder you created. There should be an icon for the program in there, too.

And you're done! To uninstall the program, just delete that folder.

Hope that helps,

Cheers,

---

### Post by kei on 2005-07-18
I have a problem. I install Ubuntu the latest one. and i wanted the network to work. the OS reconzie it as Etho0 wat does that mean?

I went to ASUS.com to get my network driver that works wit LINUX but it tell me to extract it and compile the list until it turns into Rhinefeq.o ?????? 

Motherboard is A7V8X-X 
SOCKET A

[http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx)
VIA PCI 10/100Mb Fast Ethernet Adapter driver V3.15............. intergrated
I dont know hwo to compile 

somehow the internet dont work, but i can still go to my other computer becuz its on the router.

---

### Post by Kyral on 2005-07-18
I have nearly the same Mobo and the Ethernet Adaptor works out of the box. Prolly a problem with your Router.

---

### Post by Luggy on 2005-07-19
I try and install firefox using the method Nequeo mentioned but something keeps going wrong when I perform ./firefox-installer

```

paul@ubuntu:~/Downloads$ tar xzvf firefox-1.0.5.installer.tar.gz
...
paul@ubuntu:~/Downloads$ cd firefox-installer
paul@ubuntu:~/Downloads/firefox-installer$ mkdir ~/apps/firefox1.05
mkdir: cannot create directory `/home/paul/apps/firefox1.05': No such file or directory
paul@ubuntu:~/Downloads/firefox-installer$ mkdir ~/apps
paul@ubuntu:~/Downloads/firefox-installer$ mkdir ~/apps/firefox1.05


paul@ubuntu:~/Downloads/firefox-installer$ ./firefox-installer

(firefox-installer-bin:8392): Gdk-WARNING **: locale not supported by Xlib

(firefox-installer-bin:8392): Gdk-WARNING **: can not set locale modifiers

(firefox-installer-bin:8392): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:8392): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:8392): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8392): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:8392): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (firefox-installer-bin:8392): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./firefox-installer: line 56:  8392 Aborted                 ./${BINNAME}-bin $@
``` 
what am I doing wrong

---

### Post by odin on 2005-07-20
I dont know but looks like it's a problem with the graphical interface so that leads me to this question:

Wasnt it true that the last version of firefox didnt work in ubuntu yet?

---

### Post by humina on 2005-09-16
the Xlib locale error is rampant with many x apps.  If you run locale -a, you will notice that your locale has at the top of it's list C instead of your desired language.  I still have no idea how to fix this though.

---

### Post by aysiu on 2005-09-16
[QUOTE=odin]
Wasnt it true that the last version of firefox didnt work in ubuntu yet?[/QUOTE] No, it's not true. I've installed the Mozilla version of Firefox 1.0.6 in Ubuntu many times. When I [click on the firefox-installer](http://i22.photobucket.com/albums/b337/psychocats/cf84ab22.png), [I get the install wizard](http://i22.photobucket.com/albums/b337/psychocats/2cffab86.png), and just keep clicking "next, next, next" (Windows style), and I'm all set.

Of course, since I discovered the ["Take back the Firefox and Thunderbird logos" script](http://ubuntuforums.org/showthread.php?t=34354), I use the Ubuntu version of Firefox 1.0.6.

---

