---
title: "7-zip GUI"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by TheLions on 2007-12-20
i would like to get 7-z archiver same as in the windoze. 

[IMG]http://www.7-zip.org/7zfm.png[/IMG]

How to do that?:confused:

---

### Post by maybeway36 on 2007-12-20
You don't :P
But if 7-zip is installed, File Roller (included with ubuntu) can hook on to it. Same with KDE's Ark.

---

### Post by metalpancake on 2007-12-20
you should be able to find it in add/remove programs.:)

---

### Post by RomeReactor on 2007-12-20
Hi. If you already have 7zip installed (p7zip, p7zip-full), then you'll able to create 7z archives with File-Roller, the archive manager athat comes with Gnome; press ALT+F2 and enter:
```
file-roller
```
or just highlight the files/folders you want to compress, right-click on them and select "Create Archive".
If you want File-Roller to show up in the menus, right click on the menu in the top panel, select "Edit Menus", highlight "Accessories in the left pane, and on the right check "Archive Manager".

EDIT: Too slow...

---

### Post by TheLions on 2007-12-20
i had installed 7-zip from add/remove programs but i didn't know how to create 7-z archive

thx for info

also how to see progress while unpacking file?(that would very useful when unpacking my backup ~20GB)

---

### Post by SOULRiDER on 2007-12-20
Look att he bottom of the file-roller window, you can see a sort of progress bar although i dont think it shows %. Umpacking fromt he cLI might show you progress in %

---

### Post by agibby5 on 2007-12-21
I've had alot of success with 'xarchiver' and it can be installed from the Add/Remove menu...  It was able to extract multipart rar and 7z files that file-roller couldnt.

---

### Post by mikewhatever on 2007-12-21
> **TheLions said:**
> i would like to get 7-z archiver same as in the windoze. 

[IMG]http://www.7-zip.org/7zfm.png[/IMG]

How to do that?:confused:

You'd have to use Windows then. However, it is possible to choose compression format with archive manager provided with Ubuntu.

---

### Post by TheLions on 2007-12-21
> **mikewhatever said:**
> You'd have to use Windows then. However, it is possible to choose compression format with archive manager provided with Ubuntu.

windows sucks!

i thought maybe some one compiled  the gui for ubuntu cause 7-zip is open source.

but never mind, file roller does it's work yust fine.:)

---

### Post by disturbedite on 2007-12-21
no, no, no everyone.  there is a frontend/gui for p7zip!  its called q7z and works very well.  its available on kde-apps.  (there is even a deb package available).

---

### Post by TheLions on 2007-12-21
link pleeeeeeease!

can't find it synaptec or in google:(

---

### Post by stchman on 2007-12-21
> **TheLions said:**
> i would like to get 7-z archiver same as in the windoze. 

[IMG]http://www.7-zip.org/7zfm.png[/IMG]

How to do that?:confused:


Ubuntu is able to deal with .7z archives.  Do the following in a terminal.

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

This will install the 7zip and rar packages.

Now you will be able to double click on a .7z archive and file roller will be able to unpack these archives.

Very simple.  Make sure you have the universe repositories enabled.

You can also install 7zip under WINE if you wish.

---

### Post by RomeReactor on 2007-12-21
In case you're still not satisfied wit File-Roller, here's the [q7z page]("http://k7z.sourceforge.net/7Z/Q7Z/"), and you can download it from [Google Code]("http://code.google.com/p/k7z/downloads/list"). Note: .deb package is 32-bit only ([direct link]("http://k7z.googlecode.com/files/q7z_0.6.3-1_i386.deb")).

---

### Post by TheLions on 2007-12-21
i have x64 so i tried compile it myself, i get this error:
```

root@Zvjer:/home/marko/programi/Q7Z/Build/Debian# ./Debian

Creating a Debian package using 'CheckInstall'.  Please enter your password:


checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

Warning: .spec file path "Debian/Debian.spec" not found.
Warning: Defaulting to "Debian.spec".


*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "Debian" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ Chris.Giles ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ debian ]
3 -  Version: [ 20071222 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ Debian ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]



Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

[COLOR="SandyBrown"]========================= Installation results ===========================
make: *** Nema propisa za izradu mete `install'.  Zaustavi.

****  Installation failed. Aborting package creation.[/COLOR]

Cleaning up...OK

Bye.


Finished creating a Debian package.  It has been installed and is located in 'Package'.
```

what i am doing wrong?:(

---

### Post by RomeReactor on 2007-12-21
Did you install the dependencies?
```
sudo apt-get install build-essential libqt4-core libqt4-dev python-qt4 python-qt4-dev checkinstall
```

Also, it looks like you have to run **make** from the "Build" directory, not in "Build/Debian".

---

### Post by eternicode on 2007-12-21
:rolleyes:

[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/) -- complete with DEB packages ^_^

Works well on multi-part RAR archives, too, which I wasn't able to figure out before I installed PeaZip.

Edit: :shock: ohyeah, not sure about dependencies...it installed just fine for me, but I've downloaded so much junk from the repos that anything should install fine on my system...

---

### Post by TheLions on 2007-12-22
> **RomeReactor said:**
> Did you install the dependencies?
```
sudo apt-get install build-essential libqt4-core libqt4-dev python-qt4 python-qt4-dev checkinstall
```

Also, it looks like you have to run **make** from the "Build" directory, not in "Build/Debian".

ok, installed dependencies, what next?
```

root@Zvjer:/home/marko/programi/Q7Z/Build# ls
[COLOR="DeepSkyBlue"]Arch  Debian[/COLOR]  Makefile [COLOR="DeepSkyBlue"] RedHat  Slackware  Windows[/COLOR]
root@Zvjer:/home/marko/programi/Q7Z/Build# make
pyuic4 ../Source/Main.ui -o ../Source/Main_ui.py
[COLOR="DarkOrange"]make: pyuic4: Naredba nije na&#273;ena[/COLOR] (command not found)
[COLOR="SandyBrown"]make: *** [Main_Ui.py] Greška 127[/COLOR] (Error 127)
root@Zvjer:/home/marko/programi/Q7Z/Build# 
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **eternicode said:**
> :rolleyes:

[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/) -- complete with DEB packages ^_^

Works well on multi-part RAR archives, too, which I wasn't able to figure out before I installed PeaZip.

Edit: :shock: ohyeah, not sure about dependencies...it installed just fine for me, but I've downloaded so much junk from the repos that anything should install fine on my system...

PeaZip don't have x64 .deb

---

### Post by Giorgio tani on 2007-12-27
> **TheLions said:**
> PeaZip don't have x64 .deb
Hi, I had some reports of users running successfully PeaZip on x64 systems, either using the standalone version (no installation needed) or ignoring architecture check when launching the installer.
If you prefer, you can also replace most of the performance critical binaries (p7zip, paq, lpaq...) coming with PeaZip with respective 64 bit versions available on sites of the developers: since they use the very same sintax of the 32 bit versions, PeaZip frontend will have no problem dealing with them.

---

### Post by TheLions on 2007-12-27
peazip portable works great!

Thats what I needed!!!

[IMG]http://forum.pcekspert.com/images/smilies/care.gif[/IMG] [IMG]http://forum.pcekspert.com/images/smilies/care.gif[/IMG] [IMG]http://forum.pcekspert.com/images/smilies/care.gif[/IMG] [IMG]http://forum.pcekspert.com/images/smilies/care.gif[/IMG]

---

### Post by Giorgio tani on 2007-12-28
Thank you for the positive feedback!
If you need, in the folder 'FreeDesktop_integration' in PeaZip's directory there are some instructions and examples to integrate the application in service menus through .desktop files, i.e. to directly archive or extract files from context menu entries.
Installable versions does it automatically but the same (and more) can be done by hand since most of the program's function are accessible through first command line parameter (so they can be invoked from shell, scripts, .desktop files...) with the very same syntax (which remains the same for the Windows version too).

---

