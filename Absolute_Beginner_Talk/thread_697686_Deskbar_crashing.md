---
title: "Deskbar crashing"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by prol on 2008-02-15
Desk bar crashes when I add it to the panel.Pls help

> Distribution: Ubuntu 7.10 (gutsy)
Gnome Release: 2.20.1 2007-10-19 (Ubuntu)
BugBuddy Version: 2.18.1

System: Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10300000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Gelatin
Icon Theme: Discovery

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors ---------------------
** (gnome-panel:6379): WARNING **: panel-applet-frame.c:1278: failed to load applet OAFIID:Deskbar_Applet:
Failed to resolve or extend '!prefs_key=/apps/panel/applets/applet_26/prefs;background=pixmap:14680245,-1,-1;orient=down;size=x-small;locked_down=false
Unable to open desktop file /home/roland/Desktop/firefox-1.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/roland/Desktop/firefox-1.desktop for panel launcher: No such file or directory
** (gnome-panel:6379): WARNING **: panel-applet-frame.c:1278: failed to load applet OAFIID:Deskbar_Applet:
Failed to resolve or extend '!prefs_key=/apps/panel/applets/applet_27/prefs;background=pixmap:14680245,-1,-1;orient=down;size=x-small;locked_down=false
Unable to open desktop file /home/roland/Desktop/firefox-1.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/roland/Desktop/firefox-1.desktop for panel launcher: No such file or directory
** (gnome-panel:6379): WARNING **: panel-applet-frame.c:1278: failed to load applet OAFIID:Deskbar_Applet:
Failed to resolve or extend '!prefs_key=/apps/panel/applets/applet_28/prefs;background=pixmap:14680245,-1,-1;orient=down;size=x-small;locked_down=false
Unable to open desktop file /home/roland/Desktop/firefox-1.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/roland/Desktop/firefox-1.desktop for panel launcher: No such file or directory
--------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/deskbar-applet/deskbar-applet", line 50, in <module>
    from deskbar.ui.DeskbarApplet import DeskbarApplet
ImportError: No module named DeskbarApplet

---

### Post by prol on 2008-02-15
can someone help me pls!

---

