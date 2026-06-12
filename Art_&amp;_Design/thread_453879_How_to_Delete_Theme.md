---
title: "How to Delete Theme?"
date: 2007-05-24
forum: Art &amp; Design
---

### Post by Ioky on 2007-05-24
Once you custom your own theme, how can you delete it, or is that possible to delete it? 
it is under System --> Preferences --> Theme

---

### Post by pragmatine on 2007-05-24
Your custom themes are stored in the directory:

~/.themes

Where ~ is your home directory path (/home/username).

Themes are stored in their own folders under that directory, so to delete one, simply delete the folder (which is the name of the theme you want to remove).

---

### Post by Ioky on 2007-05-24
I get there but i don't see any ~/.themes 
could it be hidden? or i looked at the wrong place?

---

### Post by Ioky on 2007-05-24
by the way i am using ubuntu studio

---

### Post by TopasPV on 2007-05-25
> **Ioky said:**
> could it be hidden?

Yes, It is hidden. Just go to View->Show Hidden Files :)

---

### Post by mcduck on 2007-05-25
> **TopasPV said:**
> Yes, It is hidden. Just go to View->Show Hidden Files :)

.or hit Ctrl-H ;)

All files and directories starting with a '.' are hidden.

---

### Post by ComplexNumber on 2007-05-25
**Ioky**
ensure that you don't delete a theme whist you are using it ;)

---

### Post by tumateix on 2009-10-27
> **ComplexNumber said:**
> **Ioky**
ensure that you don't delete a theme whist you are using it ;)

And what if I just want to do that?

I've been having some problems with the Qt-curve theme for compiz. It is enabled, and now nautilus/compizfusionicon/system arrangements/themes menu crash when I start them, so I cannot revert the changes (and set, for example, the Human o Clearlooks theme).

So I've thought about deleting the Qt-curve theme, but... is there any other solution?

I've tried to replace compiz with kwin (kwin --replace) but it's still useless.

Any suggestion, please?

Thank you!

---

### Post by Flimm on 2009-10-27
Here's how to reset all the themes to Human. Open a terminal:
```
gconftool-2 -t string -s /desktop/gnome/interface/gtk_theme Human
gconftool-2 -t string -s /desktop/gnome/interface/icon_theme Human
gconftool-2 -t string -s /apps/metacity/general/theme Human
```

---

### Post by days_of_ruin on 2009-10-27
> **Flimm said:**
> Here's how to reset all the themes to Human. Open a terminal:
```
gconftool-2 -t string -s /desktop/gnome/interface/gtk_theme Human
gconftool-2 -t string -s /desktop/gnome/interface/icon_theme Human
gconftool-2 -t string -s /apps/metacity/general/theme Human
```

Note that on 9.10 the default icon theme is Humanity instead of Human.

---

