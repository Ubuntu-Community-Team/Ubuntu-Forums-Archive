---
title: "Accpacc?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by cyrusli on 2005-12-23
Hi Everyone!

I'm fairly new with linux, haven't done anything productive with it..=)..

i'm currently using AccPac accounting software at work, its an older 6.5/7.0 version for those that are farmiliar with the program. It is the last DOS based accounting program... I'm currently running it on windows98 because of compadebility issues with 2k and XP, my question is will Accpac 6.5/7.01 run on Ubuntu, or even Linux itself. I know the newer versions do, but the boss isn't considering spending big bux on new software just yet.

Thanks!
Cyrus

---

### Post by akniss on 2005-12-23
I know nothing about the software specifically, but if it is a DOS program you can bet it won't run natively under linux.  However, there may be a way to get it working using WINE (a windows emulator, but not really an emulator).  I've not had much experience in that area, but someone might be willing to help you figure out how much trouble that might be.

---

### Post by Totzo on 2005-12-23
you could try this:

add this to your /etc/apt/sources.list

# wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

then do "sudo apt-get install wine"

then install the program by cd'ing to the directory with the setup.exe or whatever the program is called and do "wine yourfile.exe"

It may or may not work but give it a go!

---

