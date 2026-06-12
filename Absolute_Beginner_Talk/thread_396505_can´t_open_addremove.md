---
title: "can´t open add/remove"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by boonsters on 2007-03-29
Hi, pretty new to all this linux .. pretty cool though. I´m having problems opening add/remove .. from a google search was advised to enter "gnome-app-install" into terminal, which I did then got this report

Introspect error: The name org.freedesktop.AppInstall was not provided by any .s ervice files
no listening object (The name org.freedesktop.AppInstall was not provided by any  .service files)

** (gnome-app-install:6882): WARNING **: return value of custom widget handler w as not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:6882): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `s tream->cancel_func != NULL' failed

(gnome-app-install:6882): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `s tream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in  __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'

It looks like something is severely wrong, also after removing "open window" indicator from the screen, I can no longer see which windows are open ;-(

thanks for any help :-)

---

### Post by harley on 2007-03-29
did you try sudo apt-get ?

---

### Post by boonsters on 2007-03-29
yes just tried it, got a help section that I don´t understand

---

### Post by harley on 2007-03-29
ok you need to do sudo apt-get install package name here more pakage name here etc etc

sudo is used to give you root access to install files and if you do sudo --help you should see a desc of what else you can use it for

apt-get is a powerful package  tool i sure it has a apt-get --help

you must know the package name and spell it correctly

---

### Post by boonsters on 2007-03-29
ok thx, I saw the help section, but I´m not sure that I even know what "package" I´m looking for. Reading the help info only tells me that I can do certain things but not how, sorry if this all sounds a bit vague, from my other comments can you see which package I need??

---

### Post by compmodder26 on 2007-03-29
First try "sudo apt-get update".  Post the output you receive from that.

---

### Post by boonsters on 2007-03-29
sudo apt-get update
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Fetched 4B in 48s (0B/s)
Reading package lists... Done

---

### Post by compmodder26 on 2007-03-29
hmm... it appears that apt is functioning fine.  Try typing 

edit: typos

"sudo apt-get install --reinstall gnome-app-install"

---

### Post by boonsters on 2007-03-29
I just get

 "sudo apt-get reinstall gnome-app-install
E: Invalid operation reinstall"

from that one

---

### Post by compmodder26 on 2007-03-29
Yeah, sorry, I made a mistake in the command.  It should be:

"sudo apt-get install --reinstall gnome-app-install"

---

### Post by boonsters on 2007-03-29
sudo apt-get install --reinstall gnome-app-install
Reading package lists... Done
Building dependency tree... Done
Reinstallation of gnome-app-install is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

