---
title: "beginning again . . . nothing can be SAVEd"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by jambo007 on 2006-06-11
Trying to use floppies on Ubuntu installed in a Dell Latitude CPx.  I'M MISSING SOMETHING ESSENTIAL, MAYBE HAVING TO DO WITH "MOUNTING" or maybe formatting.  Existing floppies can be read on Media (just means A-drive, right, basically? I don't speak the language well), and seem to work well written in RTF.  So Ubuntu can read floppies that are created in Word.  But nothing can be SAVED on a floppy, not even newly created files that operate in Open Office and are stored in stx.  What am I missing (hope it's easy!)?

---

### Post by Xzallion on 2006-06-12
Hmm maybe the floppy isn't set to allow you to write to it.  Save your file on the hard disk, then copy it to your floppy drive using 
```
sudo cp <file_name> /media/floppy0
```
(replace <file_name> with the files name)
floppy0 = A drive in windows.  CD-ROMS, floppy's, and other removable media are mounted in /media/devicefolder so now you know a little bit more of the language.  hope that helps, and if not post back so someone more knowledgable can help you out.

---

