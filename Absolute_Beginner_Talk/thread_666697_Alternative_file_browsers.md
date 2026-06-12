---
title: "Alternative file browsers?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by whein on 2008-01-13
I've played around with Nautilus, Konqueror and Dolphin, all having some good points.  But today I realized the feature I would LOVE to have isn't in any of them.  When copying lots of files from directory A to directory B, sometimes there is already a file with the same name.  Instead of just the skip/overwrite/cancel/rename options, are there any _graphical_ based file managers that give options like:
keep newer/keep older
ignore if files match in size and/or date and/or contents and/or ?
retain these preferences for the rest of the files from this current directory, but ask again when the next directory starts copying

Also, is there any easy way to recursively set the read/write/execute attributes for a directory and all files and subdirectories?  I'm still somewhat new to chmod and the like so forgive me if this is an easy one.  Thanks guys!
-Will

---

### Post by flange on 2008-01-13
> **whein said:**
> Also, is there any easy way to recursively set the read/write/execute attributes for a directory and all files and subdirectories?  I'm still somewhat new to chmod and the like so forgive me if this is an easy one.  Thanks guys!
-Will

To use chmod recursively, add the -R flag.  The 644 numbers included below are just numbers I picked randomly.  Use whatever numbers are appropriate for your use case.  If you need some help with understanding the numbers, see [this link]("http://www.redhat.com/docs/manuals/linux/RHL-7-Manual/getting-started-guide/s1-navigating-chmodnum.html").

From your target directory's parent directory:

```
chmod -R 644 dir_name
```

From inside your target directory:

```
chmod -R 644 *
```

You can also find out more about chmod by typing

```
man chmod
```

Regarding your question about file managers, it sounds like you want a lot more power than a GUI-based file manager generally has.  Maybe someone else here knows the answer, but if was trying to solve the problem you're tackling, I'd be looking at rsync first.  Unfortunately, I don't know of any way to use rsync with a GUI.  I'm certainly not an authority on file managers, so hopefully someone else will chime in.

---

### Post by daimaru on 2008-01-13
if you want to sync files (keep newer ones etc) try 
```
sudo apt-get install unison unison-gtk
```
never used the gtk version, so i dont know what kind of options it gives you, but you could give it a try

---

### Post by SOULRiDER on 2008-01-13
Theres also rox-filer although i doubt you want that. There was one for KDE that i think you might like, it was called Kommander or Krusader, i cant remember exactly.

---

### Post by daimaru on 2008-01-13
midnight commander is also a nice app, but I'm not sure if it does any of the stuff you want. its like norton commander

---

### Post by p_quarles on 2008-01-13
> **SOULRiDER said:**
> Theres also rox-filer although i doubt you want that. There was one for KDE that i think you might like, it was called Kommander or Krusader, i cant remember exactly.
It's Krusader, and it's one of the most feature rich graphical file managers ever made. The OP should definitely give that a try.

---

### Post by daimaru on 2008-01-13
is there an equivalent for krusader under gnome? if not does it work without errors in gnome?

---

### Post by p_quarles on 2008-01-13
> **daimaru said:**
> is there an equivalent for krusader under gnome? if not does it work without errors in gnome?
Yeah, Krusader works fine with any desktop. The closest Gnome equivalent is Gnome-Commander, but that really doesn't compare to Krusader.

---

### Post by julian67 on 2008-01-13
emelfm2 is an excellent gtk2 dual pane file manager which you can customise as you like. It has its own set of commands or you can have it call any command you have available on your system. If you want to use rsync with a gui there is grsync.

---

### Post by Dr Small on 2008-01-13
I use PcManFM, and it works great.

---

