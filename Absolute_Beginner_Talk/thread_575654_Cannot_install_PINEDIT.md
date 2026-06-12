---
title: "Cannot install PINEDIT"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2007-10-14
Hi!

Trying to install pinedit to make a new table for the game, no .deb file so must compile....
./configure gives me:

checking for pinball - version >= 0.3.1... no
*** The pinball-config script installed by pinball could not be found
*** If pinball was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the PINBALL_CONFIG environment variable to the
*** full path to pinball-config.
configure: error: *** Pinball version  not found! Make sure you installed pinball - (pinball.sourceforge.net) - or try to use the --with-pinball-prefix option

This file is non-existent....

Removed piball with synaptic, downloaded source, compiled pinball... Now the file exists but get the same message anyhow, Tried to: set PINBALL_CONFIG to the proper path, but same message again....


Any suggestions etc.. welcome...


:confused:

---

### Post by Perfect Storm on 2007-10-14
Have you checked if you need to download two diffrent files? Usually Source and a data file.


EDIT: PINEDIT sounds like an editor for pinball. So you need to install it as well.

---

### Post by Ashrael on 2007-10-14
I forgot to do make install when installing pinball... doh! But now when i ./configure for pinedit i get : 

checking QTDIR... yes
checking Qt version... grep: yes/include/qglobal.h: No such file or directory
configure: error: *** Don't know how to handle this Qt major version

One step at the time....:)

---

### Post by Perfect Storm on 2007-10-14
You have installed th libqt -dev version? If so it seems that the configure file can't handle the version you have, how old is the game?

---

### Post by Ashrael on 2007-10-14
yes, that could be the problem.... 2004....
well i guess it's not possible to run that anymore, is it?


thanks..

---

### Post by Perfect Storm on 2007-10-14
Can you give me the link and I'll see it?

---

### Post by Ashrael on 2007-10-14
pinball.sourceforge.net

thanx!

---

### Post by Ashrael on 2007-10-14
Got it to work!!!

Used alien to create deb from rpm file..now it works!!!

I would attach the deb file, but it's 1,1 Mb just a little over the permitted size... just ask if you want it...


THANKS for your help!

---

### Post by Perfect Storm on 2007-10-14
Sorry, no luck. It requires some hack of the configure files.
Is it important to have the editor?

---

### Post by Ashrael on 2007-10-14
Well is it important? I would like to have more tables, like an ubuntu table for instance... ;)
I got it to start, but i still have a long  way to go....

i'll keep trying...and posting...


thx!

---

