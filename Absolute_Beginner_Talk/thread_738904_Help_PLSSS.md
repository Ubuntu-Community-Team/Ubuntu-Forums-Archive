---
title: "Help PLSSS"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ematr1x on 2008-03-29
Hey I am very new to linux aand i am using ubuntu 7.10 on my comp and it doesnt work very well When i enable my nVidia graphics driver on it and restart the comp, it loads up but the screen is just black i cant see anything.  So i reinstall it and it works fine but i cant do some of the things without the updates also when i try and load pigean it goes to the menu bar and says its loading but  nothing comes up and when i download somthing in firefox and try and open it it says unreconized even when i download stuff for ubuntu it still says unable to unpack i was wondering if anyone could help me with these problems?? THX :)

---

### Post by prismpirate on 2008-03-29
When you say you cannot do things without updates, do you mean that you are unable to update? If yes then check your internet connection to see if its working. From your pidgin unable to work, did you configure it to login to your account? If yes then maybe the internet isn't working too.

However, looking at you being able to download something, what is it for. Most probably its a tar.gz file. If its a theme, go to

System>Preferences>Appearance and drag the object into the theme selection window, and if its valid it will say the theme is correctly installed.

Or, if its a program, first move the file to your home directory. open Terminal.
You do this by going to

Application>Accessories>Terminal

Then, paste this command in there
```

gzip -cd <FILENAME> | tar xfv -

```

Subsitute filename for the name of the file


Next you paste this command:
```

tar xfvz <FILENAME>

```

Subsitute in the filename again.

Finally, just paste:

```

./configure
make
make install
make clean

```

And the program will install.


This generally works for most programs

---

### Post by ematr1x on 2008-03-29
thx i also would like to know my pidgin would log me into msn but i cant seem to open it up to talk to ppl and why cant i enable the graphics driver without the screen going blank when i reboot

---

### Post by Sef on 2008-03-29
Locked. [Duplicate Thread]("http://ubuntuforums.org/showthread.php?t=738908").

---

