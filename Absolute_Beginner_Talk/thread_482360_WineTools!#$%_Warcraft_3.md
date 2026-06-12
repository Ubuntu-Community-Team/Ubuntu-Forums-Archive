---
title: "WineTools!#$% Warcraft 3"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by pascalosti on 2007-06-23
Im going through a tutorial (how to install warcraft 3)

wget [http://download.formationos.net/winetools/winetools-0.9.4.tar.gz](http://download.formationos.net/winetools/winetools-0.9.4.tar.gz)
tar -xf winetools* 
cd winetools* 
sudo ./install

Open it with wt

I get this error:
I have libgtk-2.0  
Im guessing i have an old version of winetools, do i uninstall winetools or can i install over top of it.



no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0".
Calls to wine are executed as  "wine".
Config is /home/cc/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Enverex on 2007-06-24
Winetools is OLD. As  you can tell for a start it's trying to use GTK1 which is ancient. Winetools also doesn't work with any version of Wine newer than 0.9.9 which is also ancient. In short - Don't use Winetools.

---

