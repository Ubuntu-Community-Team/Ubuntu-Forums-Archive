---
title: "Zip problem"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Osmo on 2007-01-03
I've downloaded drivers for my USR5416 - wireless card, but I can't unzip them. The file is in -exe-format and when I type in a terminal(after changing to the right directory) : "unzip USR11g_5.0j.exe", this error shows up : "End-of-central-directory signature not found.  Either this file is not a Zip file, or it constitutes one disk of a multi-part archive. In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive"

Anyone who can help me unzipping this file?

Thanks in advance

---

### Post by bluefrog on 2007-01-03
looks like a windows program that will install the drivers in windows.

You will have to install and setup wine in order to run this .exe file.
Then once you've run it thru wine, you will have access to the drivers it installed in ~/.wine directory.

James

---

### Post by Sef on 2007-01-03
.exe is for Windows.  Ubuntu needs .deb.  Is there other downloads there?  Could you provide a link to it if you are not sure.  There is also [ndiswrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), which may be able to help you.  I believe it is available in the repositories.

---

### Post by Osmo on 2007-01-03
I was trying to install Ndiswrapper, but one of the steps([http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)) was downloading drivers for my wireless card and those drivers were in the exe-format.
And would it work with wine and, if so, where can I download it?
Or should I download other drivers, which are in .deb-format? I have tried to dowload form 2 different sites and both were in -exe-format, maybe an other site?

---

### Post by Osmo on 2007-01-03
I used this site to download my drivers :

[PHP]http://www.usr-emea.com/support/s-prod-template.asp?loc=frnc&prod=5416[/PHP]

---

### Post by bluefrog on 2007-01-03
if you are very lucky you will find them unzipped but I doubt it. Hence the solution I have given you to have them unzipped/installed using wine.

To install wine, enable universe in synaptic repository, reload and install wine.
Then in a console run:
winecfg

then
wine /path/to/the/folder-where-your-exe-is/USR11g_5.0j.exe

it should install it, then look for the files/drivers it must have installed somewhere in your .wine folder (hidden folder in your /home directory.

James

---

