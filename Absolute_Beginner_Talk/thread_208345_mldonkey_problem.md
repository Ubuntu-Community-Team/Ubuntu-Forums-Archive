---
title: "mldonkey problem"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-03
I've downloaded the rpm package and converted it to deb with alien
after that I've installed the package
I couldn't find it in the menues so I've searched for it and found it
but when I try to run the program nothing happens...

how can I run it ???

---

### Post by Jagot on 2006-07-03
Try hitting alt+f2 then type the name of the package.

---

### Post by MaximB on 2006-07-03
it still refuses to execute the file...nothing happens

---

### Post by mlind on 2006-07-03
You should install it directly from Ubuntu repositories, converting .rpm packages is
asking for trouble..

If you want more recent package, you must build it from Debian [upstream]("http://packages.debian.org/unstable/source/mldonkey")

---

### Post by catlett on 2006-07-03
Is there a binary file for it in /usr/bin? If so double click on it, this should launch it. If it does just right click anywhere on your desktop to get an options menu. Select create launcher, this will create a launcher (a shortcut in windows terms) to the file.

Just launch nautilus through Places<Computer. Then go to Filesystem. Then go to the folder usr and to it's folder bin. That's where all the binaries are kept. They are the blue squares. Double clicking on them launches the application. Actually all your applications are launched from here. Most of the time though a "shortcut" activates them for you.

---

### Post by MaximB on 2006-07-03
catlett : the second thing I did is to go there and try to run it manually (I didn't crate the luncher....what's the point if I can not run the excecute).
mlind : I downloaded this file too but it's very complicated for me to install it , I prefere to install it with a .deb file or with add/remove - but I didn't see noune of thouse options.
help still needed plz...

---

### Post by Jagot on 2006-07-03
There are packages called mldonkey-gui and mldonkey-server in the repos which are mentioned on the official mldonkey site - use those.  They are in the universe repo so if you haven't already enabled it you will need to do so.

[http://mldonkey.sourceforge.net/DownloadLinks#Third_party_cores.2C_GUIs.2C_Distributions](http://mldonkey.sourceforge.net/DownloadLinks#Third_party_cores.2C_GUIs.2C_Distributions)

---

### Post by catlett on 2006-07-03
Could you post the link to the site you got the rpm from. Maybe there is something there that will shed some light.
About synaptic. If you double click (meaniung you didn't use the terminal and dpkg -i) to install a deb.  When the deb installer starts it will alert you if there is a deb already in the repository and recommend that you use that one. Did you get that alert? Or did it install the deb and there was no prompt?

---

