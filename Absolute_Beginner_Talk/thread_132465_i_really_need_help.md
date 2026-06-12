---
title: "i really need help??"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by ubugoda on 2006-02-18
using ubuntu can i setup .rpm  and tar.gz  ???
cause i wanterd to install winetools and i checked :

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/) 


if yes how can i download and setup,,,if no what is the other ways to set it up or any other similar program.

---

### Post by bfonseca on 2006-02-18
hi this may be a dumb question but I just went to the website and found the instructions on how to install winetools, Have you tried them? If not I would start there. Tar should work for gz and that is installed already. just do a man tar with in the terminal. Hope this helps any.

**********************************************************
Installation
For RPM packages just download and on a command line type

rpm -Uvh winetools-0.9-*.rpm

For the tar.gz unpack it as root to a temporary directory and execute

install.sh

from there. It is installed in /usr/local/winetools. If you want to have it somewhere else, change $BASEDIR in wt0.9jo and findwine.

Execute by typing (Not as root!)

wt

on a shell.

Note that you should definitely start with the menu entry "Base setup" and create a new fake Windows drive. If you want to save your old .wine directory, you can use the backup funktion of WineTools. Do not use as root. Do not use as root. Do not use as root.
**********************************************************

---

### Post by nalmeth on 2006-02-18
yes you can install .rpm and tarballs

for rpms install alien in a terminal:

sudo apt-get install alien

--> go to the folder where the rpm is saved (example Desktop)

cd ~/Desktop

--> use alien to convert the .rpm into a .deb

sudo alien whatever.rpm

--> install the .deb with dpkg

sudo dpkg -i whatever.deb

installing tarballs is a little more complicated. Right-click on the tarball, and extract it where ever you wish (example desktop)

go back into terminal

sudo apt-get install build-essentials
cd ~/Desktop/whatever
./configure
make 
sudo make install

EDIT:
If the site gives you different directions, obviously use them!

to run a .sh file in a terminal,
sudo sh whatever.sh

I would recommend avoiding installing tarballs if you are newer, because usually it involves finding extra dependencies that the app needs. using apt-get, dependencies are found and installed for you. Always look for a .deb. Someone might have already made one for winetools.

---

### Post by ubugoda on 2006-02-18
THNX for the help dudes,,it worked
But for a  3 houres linux user this is not a DUMB question!!

---

### Post by nalmeth on 2006-02-18
> But for a 3 houres linux user this is not a DUMB question!!
certainly not. I think the guy was saying his own question was dumb. Glad your issue's resolved

---

### Post by Beliuntu on 2006-02-18
I think it is not a dumb question for a 3 hours user , but for u 1 week user it is so dumb..
for installing such files you must (TOSHTOFHA)..
\\:D/

---

### Post by bfonseca on 2006-02-18
Hi, I was talking about my question to you. When i said this may be a dumb question. I'm glad you were able to fix your problem.  

Brian

---

