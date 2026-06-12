---
title: "ies4 on gutsy"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2008-01-10
I'm trying to run ies4 from [here]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). When I launch I get the following cryptic message and no browser:
--------------------------
 (:~/ies4linux-2.99.0$ ./ies4linux
/home/matt/ies4linux-2.99.0/ui/pygtk/ies4linux-gtk.py:399: GtkWarning: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
  gtk.main()
ui/pygtk/python-gtk.sh: line 6:  8465 Segmentation fault      (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

------------
I'd like to not use internet exploiter at all, but i can't get turbotax to deal with mozilla on either linux or windows.

thanks

---

### Post by iDleR on 2008-01-10
I'm having the same error -.-

---

### Post by Blutack on 2008-01-10
Install it through wine-doors.
[http://www.wine-doors.org/](http://www.wine-doors.org/)
Works for me.

---

### Post by achadwick on 2008-01-11
> **scholzilla said:**
> I'm trying to run ies4 from [here]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). When I launch I get the following cryptic message and no browser:
--------------------------
[...]
------------
I'd like to not use internet exploiter at all, but i can't get turbotax to deal with mozilla on either linux or windows.

No clue about the PyGTK error, but it so happens I'm putting an Ubuntu package of ies4linux together right now. The package doesn't use the graphical installer at all, so you shouldn't get any Python errors: also, I think I've worked out the package dependencies correctly, so you shouldn't have any trouble running the thing [-o<. Install zenity first for a slightly nicer experience when running it the first time.

If you'd like to try it out, there's a Gutsy .deb [thread 636758]("http://ubuntuforums.org/showthread.php?t=636758#9") here on ubuntuforums. Let me know how you get on! ^^

---

### Post by novatotal on 2008-06-11
> **achadwick said:**
> No clue about the PyGTK error, but it so happens I'm putting an Ubuntu package of ies4linux together right now. The package doesn't use the graphical installer at all, so you shouldn't get any Python errors: also, I think I've worked out the package dependencies correctly, so you shouldn't have any trouble running the thing [-o<. Install zenity first for a slightly nicer experience when running it the first time.

If you'd like to try it out, there's a Gutsy .deb [thread 636758]("http://ubuntuforums.org/showthread.php?t=636758#9") here on ubuntuforums. Let me know how you get on! ^^

do not use ies4linux to navigate at all!
if you need ie for anything and you have a dual boot then use it from w$
on linux it will keep giving you trouble
it is only for getting a preview off web sites you are developing

---

