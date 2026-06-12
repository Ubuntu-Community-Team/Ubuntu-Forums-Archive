---
title: "WineTools won't run. &quot;error while loading shared libraries: libgtk-1.2.s&quot;"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-07-29
I installed WineTools, but I can't get it to run. Anyone know what this means?

```

charco@charco-desktop:~$ wt
detecting Wine version... done.
Drive C: is /home/charco/.wine/drive_c
Wine 0.9.17
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.17".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/charco/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
charco@charco-desktop:~$

```

If you know how to fix it, please give detailed instructions. I suck at this. Thanks.

---

### Post by Kurt` on 2006-07-29
Based on those errors, it can't find where libgtk is installed.

How did you install WineTools? Via apt-get, or did you attempt to manually install it?

---

### Post by Charco on 2006-07-29
Manual

---

### Post by Charco on 2006-07-29
How do you use this apt-get?

---

### Post by Tur Third on 2007-08-02
Easiest way to add software is to use 'Synaptic'. This installs packages specifically written for Ubuntu using a graphic interface, if you do this in a terminal screen you use the command 'get-apt'.

If you open this, do a search for 'libgtk', and have a look to see whether 1.2 is installed. Try installing and running again. I've got the same problem, but am running on 64 bit, which maybe causing a problem.

---

