---
title: "How To Hide And Find Hidden Folders? And How To Get The Trash From Panel To Desktop"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-11-22
I'd like to know? :)

---

### Post by spiderbatdad on 2007-11-22
in your home folder choose the view tab and select "show hidden files" To hide a file: right click on it to rename it, and add a . in front of the file name.
You can drag and drop icons onto your desktop. Hope this helped.

---

### Post by kevinatkins on 2007-11-22
Hi,

To hide a file or folder, precede the file or folder name with a single dot (.) To display hidden folders / files in Nautilus, press Ctrl-H

To get the Trash icon on your desktop, you need to use the GConf editor, which is a wee bit like the registry editor in Windows. To launch it, press Alt-F2, which should bring up a 'Run Application' window. In there, type in 'gconf-editor' (omit quotes) and press enter. The GConf Editor should appear. Go to Apps - > Nautilus -> Desktop (expand the 'folders' on the left side of the window) and you should see a key for 'trash_icon_visible' - just tick that and the icon will be placed on your desktop.

Cheers,

Kevin.

---

### Post by RadiationHazard on 2007-11-22
alright. i got the trash on my desktop. thanks! but i still don't know how to hide files?? :( sorry i'm retarded i guess?:confused:

---

### Post by kevinatkins on 2007-11-22
No worries. It really is as simple as adding a dot (full stop) to the beginning of the file or folder name... Do that, and the file will magically disappear from view!

---

### Post by RadiationHazard on 2007-11-22
It's MAGIC!! haha. thanks for all the help bro

---

