---
title: "rc files"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-17
I see a lot of files that have "rc" in their name.  They sem to be important, but what do they all have the "rc" in their name?  Does "rc" stand for something?

Just a few sentences about the concept of "rc" files please?

---

### Post by KhaaL on 2007-12-17
in what folder are you seeing these files?

---

### Post by movrshakr on 2007-12-17
Oh the question is far more general than about a specific folder.  I am asking, in general, what significance do I ascribe to rc files--and what does "rc" mean?

But, there are a lot of these in /etc, but many elsewhere as well.

I want to emphasize, I am not asking about a specific, single rc file, but in general, what is so special about them all that the writers decided they should be named with rc in the name?

---

### Post by asmiller-ke6seh on 2007-12-17
RC could mean Release Candidate.

Could you list some file names, as examples?

---

### Post by meindian523 on 2007-12-17
files in special folders named rc#.d are to define the apps which will be started up when booted into "#" runlevel.....supposedly apps whose names start with "S" are started while those starting with "K" are not or vice-versa.....

---

### Post by movrshakr on 2007-12-17
Requested examples (but there are many more):

/lib/modules/2.6.22-14-generic/ubuntu/media/lirc
/etc/nanorc
/etc/bash.bashrc
/etc/X11/Xsession.d/55gnome-session_gnomerc
/etc/X11/xinit/xinitrc
/etc/X11/xinit/xserverrc
/etc/init.d/rc
/etc/openoffice/sofficerc
/etc/ksysguarddrc
/etc/vim/vimrc
/etc/firefox/firefoxrc
/etc/openalrc
/etc/qt3/qt_plugins_3.3rc
/etc/qt3/qtrc
/etc/wgetrc
/etc/screenrc
/etc/inputrc
/etc/gamin/gaminrc
/etc/skel/.bashrc
/sys/class/tty/ttyrc
/sys/class/tty/ptyrc
/root/.bashrc
/dev/ttyrc
/dev/ptyrc
/dev/.udev/names/ttyrc
/dev/.udev/names/ttyrc/\x2fclass\x2ftty\x2fttyrc
/dev/.udev/names/ptyrc
/dev/.udev/names/ptyrc/\x2fclass\x2ftty\x2fptyrc
/dev/.udev/db/\x2fclass\x2ftty\x2fttyrc
/dev/.udev/db/\x2fclass\x2ftty\x2fptyrc
/home/bob/.bashrc
/home/bob/.dmrc
/home/bob/.qt/qt_plugins_3.3rc
/home/bob/.qt/qtrc

---

### Post by FuturePilot on 2007-12-17
These are usually configuration files. I'm not sure what exactly the "rc" stands for though.

---

### Post by werewolfzx8 on 2007-12-17
ha! I've always wondered the same thing, I knew they were config files, I just wanted to know why rc. Never thought to ask though.

---

### Post by lucidapparition on 2007-12-17
I don't remember what rc stand for. (Remote Control/Config?)
But rc files are the config files for various programs.
For example ~/.bashrc holds the configuration settings for bash. The ones in /etc are system wide settings, while the ones in home directories are there for the various users.

Hope that helps

---

### Post by oldos2er on 2007-12-17
I believe it means "run command."

---

### Post by mali2297 on 2007-12-17
They are configuration files for different applications. For example, in nanorc you can set different options for the editor nano. The files in /etc are system wide. If you want to make personal configurations, you should put them in files in your home directory. The rc files in your home directory usually start with a dot, like .nanorc, and are hidden.

From [jargon.net]("http://www.jargon.net/jargonfile/r/rcfile.html"):
> 
rc file /R-C fi:l/ /n./ [Unix: from `runcom files' on the CTSS system ca.1955, via the startup script `/etc/rc'] Script file containing startup instructions for an application program (or an entire operating system), usually a text file containing commands of the sort that might have been invoked manually once the system was running but are to be executed automatically each time the system starts up.


---

