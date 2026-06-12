---
title: "more wine problems"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-04-14
HI
I was following this tutorial right here [http://ubuntuforums.org/showthread.php?t=29996](http://ubuntuforums.org/showthread.php?t=29996)
So, I downloaded winetools, (different version because the link didn't work) first of all i used the tar command to unpack, but when I went and typed int "cd winetools" it didn't work. I then went into the location, and changed the unpacked name to winetools. Then it worked. But when I typed in "sudo sh install.sh" it said no such file or directory. I then simply typed in "sudo sh install" it said this
> Version: wt212jo
Release: 212
Installing WineTools to /usr/local/winetools...
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt2.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt2.mo
Installed translations for fr to /usr/local/share/locale/fr/LC_MESSAGES/wt2.mo
Installed translations for nb to /usr/local/share/locale/nb/LC_MESSAGES/wt2.mo
Installed translations for pt_BR to /usr/local/share/locale/pt_BR/LC_MESSAGES/wt2.mo
Start WineTools as *normal* user with "wt2". Don't use as root!

so I guessed that meant it went ok. But when I typed in "wt2" it came up with this
[quote]LD_PRELOAD=
found gettext in path
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine wine-0.9.35
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "wine-0.9.35".
/usr/local/bin/wt2: line 2946: [: wine-0.9.35: integer expression expected
/usr/local/bin/wt2: line 2946: [: wine-0.9.35: integer expression expected
Version of Wine is OK.
Calls to wine are executed as  "wine".
Config is /home/sam/.wine/winetools.log.
CDROM is .
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
[quote]
I looked in synaptic for the libgtk, but couldn't find it, can anyone help me?
thanks



-Sewercake

---

### Post by Jason_25 on 2007-04-14
Any reason your trying to compile stuff?  Also you are using a tutorial from 2005.  Some things change quick.  I assume your just starting out, posting in the 'absolute beginner' forum.

Try this link:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

