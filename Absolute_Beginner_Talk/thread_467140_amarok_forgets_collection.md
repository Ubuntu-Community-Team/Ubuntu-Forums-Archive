---
title: "amarok forgets collection"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by banda on 2007-06-07
amarok seems to have lost thee ability to remember the location of my music collection.. each time i run it i have to point it out and do a rescan.
earlier when amarok ran for 1st time i had pointed to the collection but the pc got hung mid way..
i've tried removing it completely and then installing it from package manager
but i don't think it helped because amarok did not ask me to give location for media like it does on the 1st run

is therre a better way to completely remove amarok and all its settings?? or to make it remember my collection??

---

### Post by muguwmp67 on 2007-06-07
To remove the user settings for amarok, you need to remove:

~/.kde/share/apps/amarok/
~/.kde/share/config/amarokrc

After removing these, the Amarok first-run wizard will run again.

---

### Post by banda on 2007-06-07
hey it worked!

thanks man:)

---

