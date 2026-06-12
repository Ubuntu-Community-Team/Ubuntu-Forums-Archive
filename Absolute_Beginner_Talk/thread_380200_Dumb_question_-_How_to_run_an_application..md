---
title: "Dumb question - How to run an application."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Chilli Bob on 2007-03-09
I've been running Ubuntu now for a week and except for some trouple getting the scanner to work, it's been bliss compared to the living hell that is Win98SE. The problem I have is in running some programs that I have downloaded. In particular, I have installed Avidemux, which, if I can get it to work, means I will never need Windows again. I downloaded the Debian package from the website (this is the package they reccomend for Ubuntu) and installed it from the desktop using the GDebi package installer. It says everything went OK, but Avidemux hasn't been added to the Applications menu, and I can't add it with Alacarte.

I know I should be able to run it from the terminal command line, but none of the documentation tells me how. This is something that Windows has over Linux, you could just look for the right folder and click on the .exe file.

If someone could explain how to find the executable (woops, I mean binary), and how to run it, it would be greatly apreciated. I ran locate and got what's below, but I don't know what is what. Thanks in advance.

rob@rob-desktop:~$ locate avidemux
/var/lib/dpkg/info/avidemux.list
/usr/local/bin/avidemux2
/usr/local/share/locale/klingon/LC_MESSAGES/avidemux.mo
/usr/local/share/locale/cs/LC_MESSAGES/avidemux.mo
/usr/local/share/locale/es/LC_MESSAGES/avidemux.mo
/usr/local/share/locale/fr/LC_MESSAGES/avidemux.mo
/usr/local/share/locale/ru/LC_MESSAGES/avidemux.mo
/usr/share/app-install/desktop/avidemux.desktop
/usr/share/app-install/icons/avidemux.png
/usr/share/doc/avidemux
/usr/share/doc/avidemux/ChangeLog
/usr/share/doc/avidemux/AUTHORS
/usr/share/doc/avidemux/COPYING
/usr/share/doc/avidemux/History
/usr/share/doc/avidemux/INSTALL
/usr/share/doc/avidemux/README
/usr/share/doc/avidemux/TODO
rob@rob-desktop:~$

---

### Post by youthforlinux on 2007-03-09
Isn't avidemux in the repos?

It is in multiverse.

use:

```
sudo aptitude install avidemux
```

Also if it is already installed you should be able to type avidemux2 in the terminal to start it. 

&

Also if you are running GNOME then Alt+F2 will bring up the run command dialog and type in avidemux2.

---

### Post by Songwind on 2007-03-09
Based on your list of files it looks like you shouse type "avidemux2" as your command line.

If you want the program to return control to the command prompt (so you can type other commands) try this:

avidemux2 &

The "&" runs the program and then returns to the console.  Very useful.

---

### Post by zukakog on 2007-03-09
You could also use Automatix to install it, along with some other useful programs.

The Automatix site at:

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

seems to be down at the moment due to ice storms in New York.

---

### Post by Chilli Bob on 2007-03-09
Thanks for the reply.

I tried adding it from the repositories using "Add/Remove" in the applications menu, and it said something along the lines of "Avidemux is not supported in any chanell", even though it was showing in the list.

I tried typing "avidemux2" at the command line and it returned....

rob@rob-desktop:~$ avidemux2
avidemux2: error while loading shared libraries: libsmjs.so.1: cannot open shared object file: No such file or directory
rob@rob-desktop:~$

I'm running Dapper, which is suppposed to work OK.

---

