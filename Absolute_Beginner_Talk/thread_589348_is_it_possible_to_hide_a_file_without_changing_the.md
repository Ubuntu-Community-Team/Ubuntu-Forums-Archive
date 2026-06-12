---
title: "is it possible to hide a file without changing the name?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2007-10-24
i have a media drive with all my music and data, but when i use windows with it for a while i get a thumbs.db and a desktop.ini in every folder it seems like. i delete them but windows puts them back in the next time.

i know how to hide a file by preceding the name with a dot, but i think that would make windows think it was deleted. is there a way to hide a file while still preserving its original name?

---

### Post by Martje_001 on 2007-10-24
For linux yes, for windows.. no. Well linux, it's more nautilus. But:

Put the name of the file you want to hide in a text-file called .hidden

---

### Post by detgar on 2007-10-24
I think you can disable thumbnail creation in windows explorer, check the Options.

You can hide files by creating a text file named .hidden in a directory and then type the name of the file you want hidden, but that would be somewhat time consuming.

---

### Post by Sonic Reducer on 2007-10-24
> **Martje_001 said:**
> For linux yes, for windows.. no. Well linux, it's more nautilus. But:

Put the name of the file you want to hide in a text-file called .hidden

in windows i typically make .trash and such hidden by right-clicking on the file and marking it hidden.

where would this .hidden file be located?

---

### Post by Sonic Reducer on 2007-10-24
> **detgar said:**
> I think you can disable thumbnail creation in windows explorer, check the Options.

You can hide files by creating a text file named .hidden in a directory and then type the name of the file you want hidden, but that would be somewhat time consuming.

could i somehow put it in the root of that directory and have it apply to all subdirectories? then i'd only need to update one master .hidden file

---

### Post by forestpixie on 2007-10-24
you can stop thumbs.db [aparently]("http://www.ofzenandcomputing.com/zanswers/98") and it seems that once you've done that and deleted them they don't return.  desktop.ini comes if you've customised the folder or view in thumbnail mode.

Depends on what you want in windows I suppose.

---

### Post by Sturmeh on 2007-10-24
You can completly disable thumb.db generation, as seen above. Also Vista includes the ability to delete all thumbs.db on the system using disc cleanup, but i'm not sure about XP...

desktop.ini is considered a windows system file, and stores data about a folder and how it was last viewed, and any icon's that were assigned to that folder.

---

### Post by Endolith on 2008-01-12
It's been requested that Nautilus be able to hide things like Thumbs.db the same way it hides Linux hidden files, but isn't happening so far.  Is there a way to hack the Windows registry or something so that Thumbs.db becomes **.**Thumbs.db?

---

