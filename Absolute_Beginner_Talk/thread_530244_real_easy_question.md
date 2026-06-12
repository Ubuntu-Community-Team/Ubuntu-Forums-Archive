---
title: "real easy question"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by spedsta on 2007-08-20
ok, a real easy question: How do i remove the icons pointing to my shares on my desktop.

I want to customise my sons desktop so that he doesnt have drive icons on the desktop, he is only 5 and may do some real damage if he just starts clicking or dragging .

Also , any other suggestions to customise a desktop for a 5 year old? Programs, etc

---

### Post by milton1 on 2007-08-20
Have you checked out Edubuntu?

[http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by asmoore82 on 2007-08-20
open a terminal and ...
```
~$ gconf-editor /apps/nautilus/desktop
```
the last option in the right pane should be "volumes-visible" - uncheck that.

---

### Post by spedsta on 2007-08-20
ok, thanks that should work for the icons. :)

I have feisty installed already , if i install edubuntu on top of that(is that possible) will it change all my settings?

And what is in edubuntu that i cant install via apt?

---

### Post by AcworthJack on 2007-08-20
one additional suggestion - you may want to use more descriptive titles to help other users.

For exmple: Desktop Icons - or Desktop Customization would have been much more informative than "real easy question".

Free support - free feedback :)

Best of luck,
John

---

### Post by asmoore82 on 2007-08-20
you can install the metapackage 'edubuntu-desktop' to convert to an edubuntu system.
both systems use the same repos so the only real difference between them is their default
themes and packages.

you may also be interested in the "lockdown" options for the panel...

```
~ $ gconf-editor /apps/panel/global
```

---

### Post by spedsta on 2007-08-20
thanks all, i found a excellent article describing exactly what i was looking for.

you can get it [here]("http://www.linuxformat.co.uk/wiki/index.php/Create_a_desktop_for_kids")

I think i will stick with installing from scratch, than rely on edubuntu, my kids arent old enuff for most of the software installed with edubuntu.

ps.I understand about the better description and will be posting with more detailed titles in the future. 

thanks once again all! :popcorn:

---

