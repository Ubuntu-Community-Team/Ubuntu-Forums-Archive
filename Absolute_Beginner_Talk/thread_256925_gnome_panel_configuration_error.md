---
title: "gnome panel configuration error?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by mandt on 2006-09-13
Hi all,
I am getting this error message when I boot up:
'An eror occurred while loading or saving configuration information for gnome panel. Some of your configuration settings may not work properly.
Type mismatch:Expected 'string got' got'int' fpr key /apps/nautilus/desktop/computer_icon_name
what do I do!!?

---

### Post by mandt on 2006-09-15
^^BUMP^^

Anyone got any advice on this??

Cheers

---

### Post by Najand on 2006-09-15
Can you rename your ".gnome" directory in your home directory to something like ".gnome.bak" and try again:
```

cd
mv -f /.gnome /.gnome.bak

```
Then restart your X by clicking Alt+Ctrl+backspace (it will also logout) and see if it errors again or not?

---

### Post by mandt on 2006-09-15
Thanks for the suggestion but still the same. any other ideas?

Steve

---

### Post by Najand on 2006-09-15
Hmm, yes.
Use
```

sudo gconf-editor

```
and change the type of
"/apps/nautilus/desktop/computer_icon_name"
to "integer" and value of "0"

---

### Post by mandt on 2006-09-15
Nope, still didn't work.
but I deleted it and restarted and now all is well:D 
How do you learn all this? It's so unsettling going from a knowledgable windows user to a total newbie again!
Thanks for the help

Steve

---

### Post by Najand on 2006-09-15
That is nice to hear it is fine now.
Well, getting used to linux iis just a matter of time...
Be patient and you can be a knoowledgable linux user too.

---

