---
title: "[SOLVED] restore menu.lst in GRUB"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by SnakeHips on 2008-04-13
I've been round and round trying to find the code to restore menu.lst from GRUB. 

I'm sure it should be something like

```
sudo rn menu.old menu.lst
```

but i just cant work out how to say that when in the GRUB menu at boot.

I want to learn this incase i ever need it :)

---

### Post by ajgreeny on 2008-04-13
I'm not quite certain what your question means but I don't think you can do excatly what you are suggesting at the grub menu point of booting up.  What you can do, however, is use a live CD, it doesn't have to be ubuntu, and follow the instructions in the txt file attached.  If that isn't what you are really meaning, come back and ask again.

---

### Post by forrestcupp on 2008-04-13
I agree that you could either do it from your Live CD, or from the recovery mode command line.

---

### Post by kellemes on 2008-04-13
> **SnakeHips said:**
> I've been round and round trying to find the code to restore menu.lst from GRUB. 

I'm sure it should be something like

```
sudo rn menu.old menu.lst
```

but i just cant work out how to say that when in the GRUB menu at boot.

I want to learn this incase i ever need it :)

assuming menu.old does exist.. you can do the following..
```
cp menu.old menu.lst
```
This will overwrite menu.lst so maybe backup first?
```
cp menu.lst menu.lst.backup
```

Maybe it's "mv" you where thinking about?
[mv]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mv")
[cp]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cp")

---

### Post by SnakeHips on 2008-04-13
> **kellemes said:**
> assuming menu.old does exist.. you can do the following..
```
cp menu.old menu.lst
```
This will overwrite menu.lst so maybe backup first?
```
cp menu.lst menu.lst.backup
```

Maybe it's "mv" you where thinking about?
[mv]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mv")
[cp]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cp")

Thank's thats EXACTLY what i was thinking about ,if menu.lst got trashed somehow then i could rename/overwrite (from GRUB) my menu.old to menu.lst.

I'll try that later ,thanks again.

---

### Post by diablo75 on 2008-04-13
Please mark this thread solved.  :)

---

### Post by SnakeHips on 2008-04-13
Ok ,not quite there yete...

from boot I hit "esc" which brings up the GRUB menu ,i select kernel xxx (recovery) and then select "root" to drop to shell. At the promt (root@desk$) i can CD to  /etc but then see no directory for X11 to go down a level (using "ls") ?

I cant see the directory /etc/X11 ?

what am i doing wrong?

---

### Post by kellemes on 2008-04-13
> **SnakeHips said:**
> Ok ,not quite there yete...

from boot I hit "esc" which brings up the GRUB menu ,i select kernel xxx (recovery) and then select "root" to drop to shell. At the promt (root@desk$) i can CD to  /etc but then see no directory for X11 to go down a level (using "ls") ?

I cant see the directory /etc/X11 ?

what am i doing wrong?

You should be able to move to the folder like so..
```
cd /etc/X11
```
```
ls
```
will show you a list of files/folders in this location..

---

### Post by SnakeHips on 2008-04-13
Your confused......I'm confused ,not only does it appear I did not make myself very clear ,I also made things worse by getting the target directory WRONG!  lmao

.....of course menu.old and menu.lst live at /boot/grub and not at /etc/whatever (i've had a bad day)

but I learnt something that cd /etc/x11 and cd /etc/X11 are not the same ;-)  thanks for all the replies and here's how i did it.

boot pc
hit "esc"
at menu select "kernelxxxx" (recovery)
then selct "root" drop to shell
you are now at root@desk$
from prompt type cd /boot/grub
type "ls" here if you want a list
or at root@desk /boot/grub 
type
cp menu.old menu.lst

voila

---

