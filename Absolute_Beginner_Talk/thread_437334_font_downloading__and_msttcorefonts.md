---
title: "font downloading  and msttcorefonts"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by lich 6222 on 2007-05-08
hi !
my third post about msttcorefonts.

Questions :

1. how I link the  msttcorefonts to programs      ?
(( I downloaded andale32.exe and use the command : "cabextract andale32.exe "
on it and got some file in a subdirectory called fonts ))
2.  what can i do to prevent other progran to try to install Msttcorefonts ?
((who just take  a lot of time and produce error ))

lich 6222

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=436185&goto=newpost](http://ubuntuforums.org/showthread.php?t=436185&goto=newpost)

ubuntu 6.10 / p4  Celron 1700/ 384mb ram

---

### Post by lich 6222 on 2007-05-08
why so much program use Msttcorefonts?

---

### Post by Bachstelze on 2007-05-08
You can do for example

```
mkdir ~/.fonts
```

You'll have a dir called .fonts in your home dir. Just put the ttf files in it, log out, log back in and the fonts should be available in your programs.

---

### Post by Medieval_Creations on 2007-05-08
This is how I installed all my TTF fonts into Ubuntu.  This also made all my fonts available to all instlled appz without any additional steps.  Hope it Helps.

1st.) In Windows, copy all the fonts from your fonts folder to a CD or flash drive, if needed. You could also just mount you windows partition too, depending on your setup.

2nd.) Have the folder open containing all your Windows fonts.

3rd.) Hit "CTRL - L". It should open a little window asking for the location you want to open.

4th.) Type "fonts:///" (without the quotes) and hit enter. It should open a window with all the current fonts installed in Ubuntu.

5th.) Select all the fonts from your Windows folder and do a copy/paste into the Ubuntu Fonts folder.

It will give you a status bar on it's progress while copying and then it will disappear as one would expect. Now the fonts have been copied over even though they do not show up, YET.

Now reboot and all your fonts should be there.

---

### Post by Michl on 2007-05-08
Strange,,, when I did it via synaptic programs that need those fonts have
access to them without me doing anything special.
M

---

### Post by Medieval_Creations on 2007-05-09
Mine is kind of a work around to the MS Core Fonts package, since it doesn't have to download anything.
Mine just takes all of your fonts from Winbloze & install them in Ubuntu.

---

