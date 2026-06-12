---
title: "recent documents"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-04-17
How do I delete it. I do not want it storing data of what files i've opened. I don't want to keep on deleting. How do I stop it from collecting the data and remove the entry in the Places menu?

---

### Post by northern lights on 2008-04-17
The recent documents are stored in ```
.recently-used.xbel
```

You've got several options.

You could change ownership of the file, alter permissions or try any of the following:

```
chmod +400 .recently-used.xbel
``` should disable it, "+600" enable it. Should that fail, you could remove it and create a directory of your own in its place, so it can't be recreated: ```
rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel
```

---

### Post by Tom--d on 2008-04-17
Tried everything you have said and it is still recording my files.

---

### Post by crjackson on 2008-04-17
I too wish this were easily tweakable.  It's not unbarable but it is annoying to me as well.

---

### Post by northern lights on 2008-04-17
How about ```
rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
chmod +400 ~/.recently-used.xbel
```

Should that still fail, do the "rm" & "touch" as above and substitue```
sudo chattr +i ~/.recently-used.xbel
``` for the last line.

---

### Post by achelis on 2008-04-17
This thread shows different ways to do it depending on the version you're running:

[http://ubuntuforums.org/showthread.php?t=91154&highlight=recent+documents](http://ubuntuforums.org/showthread.php?t=91154&highlight=recent+documents)

For Gutsy Gibbon making the file immutable (as Northern Lights shows) worked for me.

---

