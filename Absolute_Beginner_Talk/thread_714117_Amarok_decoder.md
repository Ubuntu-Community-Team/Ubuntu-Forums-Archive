---
title: "Amarok decoder"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Zini on 2008-03-03
Hi folks, im a newbie, no surpise. Anyway, i just got Amarok and when i try to play any of my pre-existing wma files it says it needs a decoder. 

Anyway, i've searched in the add/remove applications thing, and looked up here but couldnt find anything that seemed to apply to me. 

Um, im using Wubi i think as my computer has seen better days and can no longer play CDs. 

Sorry i have no idea what i need to tell you ehehe, have mercy. :)

Oh also, i downloaded the flash player but i still get popups saying it's not installed. Can i install the newest version of it running an older ubuntu? Or um is it the website that's confused?

---

### Post by rbprogrammer on 2008-03-03
to listen to windows media files, you need to install the codecs.  but since they are not "free" ubuntu does not install them by default.  so to install them, either go into synaptics and install [FONT="Courier New"]w32codecs[/FONT] or execute this command in the terminal:
```

sudo apt-get install w32codecs

```
as far as i know, i think that is the only package you need to install.  i'm also not sure if [medibuntu]("http://www.medibuntu.org/") is installed in gutsy by default, but if it isn't, you might want to check that out and install it.  it gives you media codecs that are considered "not free"

---

### Post by ajgreeny on 2008-03-03
Yes, you will definitely need the medibuntu repos for those w32codecs, so go to the site referred to above by rbprogrammer and do what it says to add them.  There are several other packages you might find useful as well as those codecs.

---

