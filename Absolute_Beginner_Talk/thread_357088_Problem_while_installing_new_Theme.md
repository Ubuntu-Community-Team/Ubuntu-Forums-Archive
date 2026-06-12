---
title: "Problem while installing new Theme"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ndefontenay on 2007-02-09
I'm trying to install the acqua theme from kde-llok.org to have my OS look like OSX.

During the installation I got the following error message:

```
nicolas@anthrax:~/acqua-3.2$ sudo sh ./install.sh
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Acqua for KDE installed.
nicolas@anthrax:~/acqua-3.2$ xhost +localhost
localhost being added to access control list
nicolas@anthrax:~/acqua-3.2$ sudo sh ./install.sh
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Acqua for KDE installed.
nicolas@anthrax:~/acqua-3.2$                
```

I can't figure out what to do to get it to work...

I've already tried xhost +localhost command

---

### Post by chuckyp on 2007-02-09
Can't you just drag the tar.gz into the theme manager?

---

### Post by ndefontenay on 2007-02-09
Oo

If it's that simple I will hate myself!

---

### Post by ndefontenay on 2007-02-09
It's still now working.
I can't believe I'm having a hard time with this after managing to install skype, proper driver for my nvidia video card and be able to watch avi and wmv movies....

I feel like I fail on the easiest part!

Here's what I've done:

1) Open kcontrol
2) Choose theme manager
3) Drag and drop the tar.gz in the theme

Result: nothing happens, No error message, nothing.

I've also tried to download the OSX docking bar from karamba (That you can find here: [http://www.kde-look.org/content/show.php?content=8030](http://www.kde-look.org/content/show.php?content=8030))

it says to uncompress somewhere and go to the theme manager an, select "Open" and locate the .theme file...

I don't have an "Open" button. In theme manager I got only an "install theme" button a "remove theme" and a "New theme".

I've tried the "Install Theme" button but when I get to the folder where it's supposed to be located, it's not finding anything...

So far it's a very frustrating experience...

---

### Post by Maestro23 on 2007-02-09
> **ndefontenay said:**
> It's still now working.
I can't believe I'm having a hard time with this after managing to install skype, proper driver for my nvidia video card and be able to watch avi and wmv movies....

I feel like I fail on the easiest part!

Here's what I've done:

1) Open kcontrol
2) Choose theme manager
3) Drag and drop the tar.gz in the theme

Result: nothing happens, No error message, nothing.

I've also tried to download the OSX docking bar from karamba (That you can find here: [http://www.kde-look.org/content/show.php?content=8030](http://www.kde-look.org/content/show.php?content=8030))

it says to uncompress somewhere and go to the theme manager an, select "Open" and locate the .theme file...

I don't have an "Open" button. In theme manager I got only an "install theme" button a "remove theme" and a "New theme".

I've tried the "Install Theme" button but when I get to the folder where it's supposed to be located, it's not finding anything...

So far it's a very frustrating experience...

[http://www.kde-look.org/help/index.php?type=9](http://www.kde-look.org/help/index.php?type=9)

---

