---
title: "Terminal problem with code"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by gingin on 2007-03-21


Guys I would like to ask you help me out in there..

Instalation shuld be:
[PHP]sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
You may need to wait a few mintues for this to complete.[/PHP]
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I have downloaded ati drivers in to home directory
[PHP]gin@laptop:~$ dir
ati-driver-installer-8.34.8-x86.x86_64.run  Desktop  Examples[/PHP]
In terminal I can see installer.

[COLOR="Black"]Guys how to get code lines to make terminal undersand there those drivers are ?[/COLOR]

Doesn't what I do terminal says as where is no such directory .... :confused:

---

### Post by david_kt on 2007-03-21
Did you try:

[INDENT]bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy[/INDENT]

or

[INDENT]bash ./ati-driver-installer-8.34.8-x86.x86_64.run --buildpkg Ubuntu/edgy[/INDENT]

?
For your case, it should be the second one, not the first i.e. you must change <version> to the exact version of your installer.

DK

---

### Post by gingin on 2007-03-21
I did this David
[PHP]    bash ./ati-driver-installer-8.34.8.run --buildpkg Ubuntu/edgy [/PHP]

I think know I can see mistake(may be) i haven't typed[COLOR="Black"]** x86.x86_64**[/COLOR]. But I will tray do all line wich is [COLOR="Black"]**8.34.8-x86.x86_64.run**[/COLOR]

---

