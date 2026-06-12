---
title: "unreadable fonts in emacs"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by goodmanbrown on 2007-02-19
I just installed Edgy on my new laptop.  Fonts in general look fine, but fonts in emacs are nearly illegible.  I don't think this is just a matter of the emacs font not being aliased (unless unaliased fonts are illegible on an LCD screen-- this is my first LCD).  The characters look squished vertically, and seem to have pixels mixing.

This is a nearly clean install of Edgy, with some things, including the MS core fonts, installed via EasyUbuntu.  Plus emacs, of course.

Any help in getting emacs to work would be appreciated.  I've got some work I need to do in LaTeX, and really don't want to have to learn a new text editor!

---

### Post by nereid on 2007-02-19
Emacs and fonts are really terrible. But I would recomment the terminus font

```

(set-face-font 'default "-*-terminus-*-r-*-*-14-*-*-*-*-*-iso8859-*")

```

Put this in your .emacs file and you should have a nice font (running on a TFT with 1280x1024 resolution).

---

### Post by goodmanbrown on 2007-02-20
Thanks!

I changed the font to Courier in my .emacs file, and text is now legible.  However, emacs' startup time has been slowed from nearly instantaneous to about ten seconds.  Is that normal behavior?

---

### Post by nereid on 2007-02-20
Normally not. What have you entered in your .emacs file (or just post your whole .emacs file)?

---

### Post by goodmanbrown on 2007-02-21
The only entry in my .emacs file is this:

```
(set-face-font 'default "-Adobe-Courier-Medium-R-Normal--17-120-100-100-M-100-ISO8859-1")
```

I got the huge font string by switching to Courier once inside emacs via shift+left-click, choose font, and then, inside *scratch* running

```

(frame-parameter nil 'font)
```

to see the font string emacs was using to show the Courier font.

I did get the Terminus font that you recommended to work, and it exhibited the same slow startup time as Courier.

---

### Post by nereid on 2007-02-21
This is really strange as you have only one entry in your .emacs file (the more content the longer needs emacs to start). BTW these font strings are the Unix font strings. You can get them through xfontsel (you can also look at your installed fonts this way). 

Do you use the normal emacs package, the snapshot or a cvs installation? Besides emacs takes its time to start up, it isn't the fastest car in the city.

---

