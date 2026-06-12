---
title: "Starting the BitTorrent GUI Application"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by chuntley on 2007-07-05
Running Ubuntu Feisty,  I have installed the Gnome BitTorrent application and GUI from the Add/Remove Applications Manager.

My problem is, I don't know how to launch it now.  :o  Should this show up in the applications list or does it need to start from the terminal?  If so, what would I type at the terminal prompt?

Thanks for any help!!

---

### Post by illu45 on 2007-07-05
If you installed it using the Add/Remove applications app, it should appear in the Applications List, probably under Network. If it doesn't work there, you can launch it by pressing ALT+F2, typing in the name of the application (In this case, probably BitTorrent) and pressing Enter.

Hope that helps,
illu45

---

### Post by quixotic-cynic on 2007-10-06
You can type ```
btdownloadgui
``` or ```
btdownloadgui.bittorrent
``` Unfortunately it wont do much as it doesn't have a queue or anything so needs to be told to open *with* a particular .torrent file for it to do anything.

If you get the problem ```
Could not load wxPython. In order to use this script,
you must have wxPython installed.  It is available in
the package libwxgtk2.4-python.
```

The you can use ```
sudo gedit /usr/bin/btdownloadgui
``` and change ```
wxversion.select('2.4')
``` to ```
wxversion.select('2.6')
```

(Version 3.4.2 is current in the repos, queuing was introduced in 3.9.1...)

---

