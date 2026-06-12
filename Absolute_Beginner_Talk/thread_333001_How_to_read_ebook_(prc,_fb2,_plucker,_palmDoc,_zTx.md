---
title: "How to read ebook (prc, fb2, plucker, palmDoc, zTxt, oeb)"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by david_kt on 2007-01-06
I have an ebook (Palm Resource Code) and having difficulties in reading it. Finally I could read it using FBReader.

Previously I have tried to run mobipocketreader using wine, pyrite-publisher, thoutreader and dotreader without anyluck. So, I thought my experience installing FBReader would be usefull for others.

Below is the link I use to download FBReader and neccesary programs:

[INDENT][http://only.mawhrin.net/fbreader/desktop/](http://only.mawhrin.net/fbreader/desktop/)[/INDENT]

First of all, you must install expat, libbz2 and enca. Please see below link for to download them:
[INDENT][http://expat.sourceforge.net/](http://expat.sourceforge.net/)
[http://sources.redhat.com/bzip2](http://sources.redhat.com/bzip2)
[http://trific.ath.cx/software/enca](http://trific.ath.cx/software/enca)[/INDENT]

I did not install bzip2 as I thought it is already available in ubuntu. The interesting thing is when installing enca, it requires us to use "make check" before installing. So the script is:

[INDENT]./configure
make
make check
sudo make install[/INDENT]

Please run those scripts one by one.

To install expat, just do the usual configure, make, sudo make install.

As I have install QT, I choose to download:

[INDENT][http://only.mawhrin.net/fbreader/desktop/fbreader-qt-0.7.4q.tgz](http://only.mawhrin.net/fbreader/desktop/fbreader-qt-0.7.4q.tgz)[/INDENT]

If you have not install QT, you should install it first. It is available in ubuntu.
But to install FBReader, I do it manually as I did not know how to extract it directly to appropriate folder:

Extract fbreader-qt-0.7.4q.tgz.
Copy each files/folders to appropriate folders:

[INDENT]/usr/local/bin
/usr/local/lib
/usr/local/share
[/INDENT]
You should use sudo when copying it.

To run FBReader, just type FBReader in terminal. If you want to have it in the menu, do below step:
[INDENT]
 sudo gedit /usr/share/applications/FBReader.desktop[/INDENT]

Copy below scripts to it:

[INDENT][Desktop Entry]
Name=FBReader
Comment=To read ebook
Categories=Application;Network
Exec= FBReader
Type=Application

# if you want to have a custom icon, edit:
# Icon=yourfile.png (or other icon files, save it in /usr/share/pixmaps)
Icon=gdict.xpm[/INDENT]

You should have a menu in application> internet. If you want want to move it to another place, please use alacarte menu editor.

DK

---

### Post by wdev on 2008-03-30
Sometimes you find an old topic with a very interesting thing - exactly what are you looking for. And, back to the topic, FBReader is now available from it's own repositories, so forget about anythig written above. Just take a look at: [http://www.fbreader.org/desktop/debian.php](http://www.fbreader.org/desktop/debian.php)

---

