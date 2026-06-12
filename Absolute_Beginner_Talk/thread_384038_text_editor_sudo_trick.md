---
title: "text editor sudo trick"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by thejones on 2007-03-14
ok here is the deal. i found a little trick (in a guide somewhere) to make the text editor open in sudo mode. it was the easiest way to edit write protected files (such as the grub boot file).

but unfortunatly, i had to reinstall ubuntu in an attempt to get my wireless card to work, and i forgot how i did it the first time.

i remember that it was a very simple command added to the front of the launcher. but i cant seem to remember what it was. 

does this sound familiar to any of you guys?

---

### Post by brettg on 2007-03-14
That would be sudo from the console or gksu from gnome

eg. sudo vi file.txt

or ALT-F2 gksu gedit

---

### Post by fusiachi on 2007-03-14
...

edit: above post beat me to the punch.  Is there an option to delete posts?

---

### Post by aysiu on 2007-03-14
```
sudo nano *nameoffile*
``` ```
gksudo gedit *nameoffile*
``` ```
kdesu kate *nameoffile*
```

---

### Post by thejones on 2007-03-14
the thing i was thinking of was actualy a tag that you put in the begining of the launcher. but those work too.

well thats linux for ya. more than one way to skin a cat.

sorry aysiu.... :p

---

### Post by brettg on 2007-03-14
you can put gksu at the beginning of a launcher in the gnome menu ( assume that this is what you mean) , so that is probably what you are recalling.

---

### Post by thejones on 2007-03-14
> **brettg said:**
> you can put gksu at the beginning of a launcher in the gnome menu ( assume that this is what you mean) , so that is probably what you are recalling.


YES!!

thats it. thank you.

and thanks to everyone else too. i may need that info one day as well :D

---

