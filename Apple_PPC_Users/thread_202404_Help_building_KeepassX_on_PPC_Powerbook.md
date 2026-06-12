---
title: "Help building KeepassX on PPC Powerbook"
date: 2006-06-23
forum: Apple PPC Users
---

### Post by shamael on 2006-06-23
I learned to love Keepass on Windows so I am very glad that someone finally ported it to Linux (and Mac) but unfortunately the .dep package and the "bundle" are only for i386 so there's no other choice for me than compiling it from source.
I followed the guidelines on their website, double checked all the Qt requirements, then proceeded with qmake and then make. That's where I get problems... This is the terminal output:

[PHP]shamael@shamael-ubuntu-G4:~/Desktop/KeePassX-0.2.1$ make
cd src && make -f Makefile
make[1]: Entering directory `/home/shamael/Desktop/KeePassX-0.2.1/src'
Makefile:634: warning: overriding commands for target `../build/EditGroupDlg.o'
Makefile:451: warning: ignoring old commands for target `../build/EditGroupDlg.o'
Makefile:645: warning: overriding commands for target `../build/SearchDlg.o'
Makefile:462: warning: ignoring old commands for target `../build/SearchDlg.o'
Makefile:651: warning: overriding commands for target `../build/AboutDlg.o'
Makefile:442: warning: ignoring old commands for target `../build/AboutDlg.o'
Makefile:658: warning: overriding commands for target `../build/SettingsDlg.o'
Makefile:469: warning: ignoring old commands for target `../build/SettingsDlg.o'
Makefile:668: warning: overriding commands for target `../build/SimplePasswordDlg.o'
Makefile:492: warning: ignoring old commands for target `../build/SimplePasswordDlg.o'
Makefile:676: warning: overriding commands for target `../build/DatabaseSettingsDlg.o'
Makefile:477: warning: ignoring old commands for target `../build/DatabaseSettingsDlg.o'
Makefile:684: warning: overriding commands for target `../build/PasswordDlg.o'
Makefile:485: warning: ignoring old commands for target `../build/PasswordDlg.o'
Makefile:697: warning: overriding commands for target `../build/EditEntryDlg.o'
Makefile:505: warning: ignoring old commands for target `../build/EditEntryDlg.o'
Makefile:707: warning: overriding commands for target `../build/PasswordGenDlg.o'
Makefile:515: warning: ignoring old commands for target `../build/PasswordGenDlg.o'
Makefile:715: warning: overriding commands for target `../build/SelectIconDlg.o'
Makefile:523: warning: ignoring old commands for target `../build/SelectIconDlg.o'
Makefile:803: warning: overriding commands for target `../build/moc_EditGroupDlg.o'
Makefile:742: warning: ignoring old commands for target `../build/moc_EditGroupDlg.o'
Makefile:810: warning: overriding commands for target `../build/moc_SearchDlg.o'
Makefile:749: warning: ignoring old commands for target `../build/moc_SearchDlg.o'
Makefile:814: warning: overriding commands for target `../build/moc_AboutDlg.o'
Makefile:737: warning: ignoring old commands for target `../build/moc_AboutDlg.o'
Makefile:817: warning: overriding commands for target `../build/moc_SettingsDlg.o'
Makefile:752: warning: ignoring old commands for target `../build/moc_SettingsDlg.o'
Makefile:823: warning: overriding commands for target `../build/moc_SimplePasswordDlg.o'
Makefile:765: warning: ignoring old commands for target `../build/moc_SimplePasswordDlg.o'
Makefile:829: warning: overriding commands for target `../build/moc_DatabaseSettingsDlg.o'
Makefile:758: warning: ignoring old commands for target `../build/moc_DatabaseSettingsDlg.o'
Makefile:833: warning: overriding commands for target `../build/moc_PasswordDlg.o'
Makefile:762: warning: ignoring old commands for target `../build/moc_PasswordDlg.o'
Makefile:840: warning: overriding commands for target `../build/moc_EditEntryDlg.o'
Makefile:772: warning: ignoring old commands for target `../build/moc_EditEntryDlg.o'
Makefile:848: warning: overriding commands for target `../build/moc_PasswordGenDlg.o'
Makefile:780: warning: ignoring old commands for target `../build/moc_PasswordGenDlg.o'
Makefile:854: warning: overriding commands for target `../build/moc_SelectIconDlg.o'
Makefile:786: warning: ignoring old commands for target `../build/moc_SelectIconDlg.o'
Makefile:902: warning: overriding commands for target `../build/moc/moc_EditGroupDlg.cpp'
Makefile:869: warning: ignoring old commands for target `../build/moc/moc_EditGroupDlg.cpp'
Makefile:905: warning: overriding commands for target `../build/moc/moc_SearchDlg.cpp'
Makefile:872: warning: ignoring old commands for target `../build/moc/moc_SearchDlg.cpp'
Makefile:908: warning: overriding commands for target `../build/moc/moc_AboutDlg.cpp'
Makefile:866: warning: ignoring old commands for target `../build/moc/moc_AboutDlg.cpp'
Makefile:911: warning: overriding commands for target `../build/moc/moc_SettingsDlg.cpp'
Makefile:875: warning: ignoring old commands for target `../build/moc/moc_SettingsDlg.cpp'
Makefile:917: warning: overriding commands for target `../build/moc/moc_SimplePasswordDlg.cpp'
Makefile:884: warning: ignoring old commands for target `../build/moc/moc_SimplePasswordDlg.cpp'
Makefile:920: warning: overriding commands for target `../build/moc/moc_DatabaseSettingsDlg.cpp'
Makefile:878: warning: ignoring old commands for target `../build/moc/moc_DatabaseSettingsDlg.cpp'
Makefile:923: warning: overriding commands for target `../build/moc/moc_PasswordDlg.cpp'
Makefile:881: warning: ignoring old commands for target `../build/moc/moc_PasswordDlg.cpp'
Makefile:926: warning: overriding commands for target `../build/moc/moc_EditEntryDlg.cpp'
Makefile:887: warning: ignoring old commands for target `../build/moc/moc_EditEntryDlg.cpp'
Makefile:929: warning: overriding commands for target `../build/moc/moc_PasswordGenDlg.cpp'
Makefile:890: warning: ignoring old commands for target `../build/moc/moc_PasswordGenDlg.cpp'
Makefile:932: warning: overriding commands for target `../build/moc/moc_SelectIconDlg.cpp'
Makefile:893: warning: ignoring old commands for target `../build/moc/moc_SelectIconDlg.cpp'
make[1]: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
make[1]: Leaving directory `/home/shamael/Desktop/KeePassX-0.2.1/src'
make: *** [sub-src-make_default] Error 2
[/PHP]

qmake didn't output anything so I suppose everything went fine... enabling debugging on it gives a lot of info I don't know how to interpret (btw, how do I print to a file instead of standard console output?) :-k

Ideas anyone?


P.S. I'm running dapper and Qt version is 4.1.2

---

### Post by Ptero-4 on 2006-06-23
I got the problem. KeepassX is made for Qt3 and Qt3 apps won't compile/run on Qt4. Your options are or wait for KeepassX to be ported to Qt4 or look around to see if there is a legacy Qt3 compatibility package for ubuntu (or in source) and install it first.

---

### Post by shamael on 2006-06-24
As far as I've seen from their website, KeepassX uses Qt4 for 0.2.0 versions and higher (mine is 0.2.1) and Qt3 for earlier ones.
In fact, these are the prerequisites listed for using the source code:

    * Qt 4.1.0
    * libQt3Support.so.4
    * Modules: QtCore, QtGui, QtXml, QtSql, QtNetwork and includes
    * Devel-Tools (qmake, uic, moc)
    * X11 with Xlib-includes
    * optional, if auto-type function is activated: XTest extention with includes


Qt3 is in the repos and when I tried using that (before reading about Qt4) make halted saying that my Qt version (3.3.6) was too old...:(

---

### Post by shamael on 2006-06-26
bump... :(

---

### Post by PatoLucas on 2006-07-01
Hi!

I had the same problem (on an iBook, but it should be the same)

Now it's working:

[LIST]
[*]Make sure no qt3 dev tools are installed. Only qt4.

[*]Use the svn version (0.2.2)

[*]Install all qt4 packages (including debug and debug-dev)
[/LIST]

It even opens databases from the windows version!

---

