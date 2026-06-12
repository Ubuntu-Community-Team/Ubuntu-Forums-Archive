---
title: "Wine Problems"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-03-06
Hello, i installed Wine through the synpathic package manager. i did not notice any change and when i clicked on a .exe i hit "open with" and wine was on an option. So i removed it and then re installed it with the add/remover programs tool. and still the same problem any body have a clue? Thanks

---

### Post by steven8 on 2007-03-06
Okay.  You don't 'see' wine, but wine is there.  If you want to run an installer, or the exe afterwards, type winefile in a terminal, and hit enter.  This will bring up a windows like browser.  If you have a cdrom with an installer in the drive, navigate to the cdrom drive media>cdrom, find the installer and double click it.  Allow the program to install to c:Program Files\(etc.), as you would in windows.  This creates a file system of /home/.wine(this is a hidden folder)/drive_c/Program Files/(Your Program Folder)/(Your Program).

Once installed, open winefile again, browse to your file via the path I just spelled out, and double-click the exe.

You can also use, winecfg to set some properties of wine and how it plays your program(s).  For example, if your program was made for win98, you can tell wine to run it as a win98 program for optimal running.

---

