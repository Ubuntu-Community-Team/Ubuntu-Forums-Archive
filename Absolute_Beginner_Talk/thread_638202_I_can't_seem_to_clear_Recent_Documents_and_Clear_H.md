---
title: "I can't seem to clear Recent Documents and Clear History in file browser..?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-11
Hi,

 i wanna do:
1. remove the recent Documents from the menu so you can't see it.
2. remove the Clear History so it doesn't display the folders i visited in File Browser..
3. remove any history in totem.

i tried some suggestions in the forum but the recent documents keep coming back..

any help appreciated...

thanks.

---

### Post by spiderbatdad on 2007-12-11
if you are using Firefox, Tools-->Clear Private Data.
for your folders in Nautilus there is Go--> Clear History

---

### Post by hopelessone on 2007-12-11
perhaps the question was mis-understood...

i wanna always not have to manually clear docs... so it always displays nothing...
in the[COLOR="Red"] gnome menu, file browser and totem[/COLOR]..

i already set up firefox in preferences to clear everything on exit..

taa...

---

### Post by cjjack56 on 2007-12-11
I understand what you were trying to do and managed to accomplish this but went one better. I managed to remove the applications, places and system selections from the panel. My question now is how do I get it back like it was as a reboot didn't work. I'm a total newb and was searching but this was as close as I got to the situation. Once I get it back how would I go about removing the recent dockuments selection from the menu ?

---

### Post by hopelessone on 2007-12-11
> I managed to remove the applications, places and system selections from the panel. My question now is how do I get it back

right click the panel and add to panel...at the bottom select main menu...

---

### Post by hopelessone on 2007-12-11
News:
from post [http://ubuntuforums.org/showthread.php?t=375510](http://ubuntuforums.org/showthread.php?t=375510)
Brucevdk wrote:
There's no real fix available (though I presume there will be shortly), the workaround as described in bug report #87472 at Launchpad is to remove the file and create a directory instead.
```
rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel
```

works !! 

questions 1 & 3 are solved...

Now only question 2 is unsolved...

---

### Post by hopelessone on 2007-12-13
anyone know 
2. remove the Clear History so it doesn't display the folders i visited in File Browser..?

or where the history file is kept?

---

### Post by ross9885 on 2007-12-21
It's late now but tomorrow I'll get the Nautilus code and grep around for history related strings.

---

### Post by hopelessone on 2007-12-23
Great News...Thanks a bunch..

Good Night..

---

### Post by hopelessone on 2008-01-06
2. remove History so it doesn't display the files  i visited in File Browser..?
pwease..

---

