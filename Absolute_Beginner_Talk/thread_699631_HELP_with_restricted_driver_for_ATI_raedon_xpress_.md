---
title: "HELP with restricted driver for ATI raedon xpress 200"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by irunwithknives on 2008-02-17
When I install the restricted driver, my computer starts normally, but i get no display.

What do I do?
(im using a different computer right now)

---

### Post by Mjölner on 2008-02-17
do you get to the login screen?

---

### Post by irunwithknives on 2008-02-17
no

just a blank screen through and thorough

but I could tell that it was to the logon screen cause of the system beep when I pressed right and left but not when I pressed up or down

then, when I was logged in, I pressed my keyboard shortcut for the media player, and played a song
but I cant see anything

---

### Post by zipperback on 2008-02-17
Do you see the boot up splash screen?

Is this is desktop or a laptop?

Which version of Ubuntu specifically are you using?

Is this the 32 bit or 64 bit version?

- zipperback
:popcorn:

---

### Post by irunwithknives on 2008-02-17
no

just a blank screen through and thorough

but I could tell that it was to the logon screen cause of the system beep when I pressed right and left but not when I pressed up or down

then, when I was logged in, I pressed my keyboard shortcut for the media player, and played a song
but I cant see anything


this is a desktop, and I am using Gusty (7.10 i guess?)

and I think it is the 32 bit version, but Im not sure

---

### Post by Mjölner on 2008-02-17
With the installation the new drivers you have probably changed the " /etc/X11/xorg.conf " file
Boot into the Ubuntu recovery mode and restore the backup.
Can you navigate in a text based system?

---

### Post by zipperback on 2008-02-17
Boot into recovery mode and then enter:

dpkg-reconfigure xserver-xorg

You should then be able to reconfigure and get your system up and running.

Please let me know if this works for you.

- zipperback
:popcorn:

---

### Post by irunwithknives on 2008-02-17
it worked!!!!

THANK YOU SOOOOOOO MUCH!!!!

---

