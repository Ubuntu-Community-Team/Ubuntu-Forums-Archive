---
title: "lost option in Breezy upgrade"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-02-03
I've just upgraded from Hoary to Breezy (which was pretty simple) but I've lost a feature -

in Hoary you right clicked the desktop and the first option in the pop up menu was Open Terminal, which I thought was toptastic. :-D 

But in Breezy this is gone and I've had to drag a terminal icon onto the taskbar thingo at the bottom.

It's minor I know (but annoying) - is there any way to quickly get that option back into the right click menu?

BHT

---

### Post by jamesford on 2006-02-03
it can be added by finding nautilus-open-terminal in synaptic if i remember correctly

---

### Post by Mustard on 2006-02-03
oops never mind..misread the above post. :)

---

### Post by Bubba Ho-Tep on 2006-02-03
Mmmmmm can't see anything in synaptic and there ain't any option I can see in the gnome to edit that menu.

I'm sure i'll learn how to manually edit the sucker later, its just a shame cos opening a terminal from anywhere on the desktop was really convenient.

BHT

---

### Post by jamesford on 2006-02-03
you may have to enable all repositories
[http://ubuntuguide.squarecows.com/doku.php#repositories](http://ubuntuguide.squarecows.com/doku.php#repositories)

---

### Post by Bubba Ho-Tep on 2006-02-03
Aha. My Linbox ain't networked as yet - that's a job for tomorrow.

Thanks for the help

BHT

---

### Post by Mustard on 2006-02-03
Its definitely there in the universe repository.

```
mustard@slave:~$ apt-cache show nautilus-open-terminal
Package: nautilus-open-terminal
Priority: optional
Section: universe/gnome
Installed-Size: 372
Maintainer: Dan Korostelev <nadako@gmail.com>
Architecture: i386
Version: 0.4-0ubuntu1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libgconf2-4 (>= 2.9), libglib2.0-0 (>= 2.7.1), libgnome-desktop-2 (>= 2.9.91), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.11.3), libgtk2.0-0 (>= 2.6.0), libice6, libnautilus-extension1 (>= 2.9.1), liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.8.1), libpopt0 (>= 1.7), libsm6, libstartup-notification0 (>= 0.8-1), libxml2 (>= 2.6.17), zlib1g (>= 1:1.2.1)
Filename: pool/universe/n/nautilus-open-terminal/nautilus-open-terminal_0.4-0ubuntu1_i386.deb
Size: 15372
MD5sum: 041535eb497b8847c2ddb2eb7965717e
Description: open terminal in any folder from Nautilus
 This is an extension for Nautilus (file manager for
 GNOME desktop) that provides a menu option for any
 local folder object to open a terminal in that folder.
 .
 Homepage: http://manny.cluecoder.org/packages/nautilus-open-terminal/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by Bubba Ho-Tep on 2006-02-04
Ok, I downloaded it, all went well etc etc.

But er where did it go? I was expecting to install it and bingo the right click menu would have the option again. Do I need to reboot or something to get it to do its thing?

This is kinda my biggest problem in Linux at the mo - i install something and then can't find how to run the bloody thing. Sometimes typing the name in a terminal runs whatever I've installed most times it doesn't.

I guess coming from Windows I'm expecting shotcuts on the desktop or in a menu somewhere. It is a bit of a mission finding how to run stuff:)

---

