---
title: "FF under wine: ugly tiny fonts"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by odzx on 2006-09-18
I did post an identical question on the nozilla forum but since this could be a wine problem I'm posting it hre to.
I've installed windows FF under wine on ubuntu daper becaus I've been having freezes of linux FF when viewing pages with flash. windows FF seems to work ok with wine but the fonts in the menus are very small, and hebrew fonts looks terrible in the menus and also very small and ugly in the search bar. I tried playing around a little bit with the userchrome.css file and was able to change the size of the fonts in the menus but the fonts still dont look right. hebrew fonts still look very bad and very hard to read + the fonts typed inside the the searchbar are still very small.
does anyone have any ideas what could be done to fix that?

---

### Post by JNowka on 2006-09-18
You will want to download and install the Microsoft Fonts for windows.  The fonts you will want are as follows:
andale32.exe
arial32.exe
arialb32.exe
comic32.exe
courie32.exe
georgi32.exe
impact32.exe
times32.exe
trebuc32.exe
verdan32.exe
webdin32.exe

All of these can be somewhere on microsofts website I believe.

The problem with the fonts is that wine comes with some, or uses the fonts that come with the linux box.  Im not sure but they are ugly.  This should do the trick.

If you don't want to do all of these the hard way, I would suggest downloading winetools just so you can install the fonts.  It has a setup so you can download and install all needed windows fonts.  As for anything else, you are at your own risk, because somethings just don't install since about wine 0.9.5.

Good Luck
JNowka

---

### Post by moore.bryan on 2006-09-18
*i've read downloading/installing the new ff2.0b2 solved the problem... not sure how efficient running ff through wine is....*

---

### Post by JNowka on 2006-09-18
Very if you ever plan on visiting a site that is using shockwave.  Other than that, its not a good idea.

---

### Post by odzx on 2006-09-19
> **JNowka said:**
> You will want to download and install the Microsoft Fonts for windows.  The fonts you will want are as follows:
andale32.exe
arial32.exe
arialb32.exe
comic32.exe
courie32.exe
georgi32.exe
impact32.exe
times32.exe
trebuc32.exe
verdan32.exe
webdin32.exe

All of these can be somewhere on microsofts website I believe.

The problem with the fonts is that wine comes with some, or uses the fonts that come with the linux box.  Im not sure but they are ugly.  This should do the trick.

If you don't want to do all of these the hard way, I would suggest downloading winetools just so you can install the fonts.  It has a setup so you can download and install all needed windows fonts.  As for anything else, you are at your own risk, because somethings just don't install since about wine 0.9.5.

Good Luck
JNowka
thanx JNowka for the help. unfotunatly after installing wintools and the fonts, firefox does not show any hebrew fonts in the dropdown menu and i can not right any hebrew in the browser. all i get is ??????
any ideas?

---

### Post by odzx on 2006-09-23
ok some progress.
ater messing around with wine with no sucsses i finaly realized that my local setting where wrong. after fixing this problem ie4linux is working fine and lets me write hebrew and is even showing the menus ok. nevertheless the problem with FF ander wine still remains. now instead of showing ugly fonts or ????? its showing me gibrish when writing hebrew.
if anyone have any ideas please help me out here. any atempt to help will be much appreciated.
thanks.

---

### Post by podunk on 2006-09-23
I'm very new at this, and I've found that most of my problems are caused by moi. :-) And often the best way to fix them is to uninstall what ever and try it again.

As far as font size goes - will the <CTRL> <+> keys not work under wine to adjust text size?

---

