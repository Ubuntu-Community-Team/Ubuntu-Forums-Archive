---
title: "Video file preview thumbnails"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-09
In my video folder none of my videos show a preview thumbnail. Just a roll of film icon, It use to show preview. Did I uncheck a setting on accident or something?

---

### Post by rune0077 on 2008-01-09
Check this: from Nautilus Edit > Preferences and go to Preview. Make sure the Other Previewable Files is not set to Never. Otherwise you'll need to open gconf editor (configuration editor) and go to desktop > gnome > thumbnailers - from here you can check/uncheck what you want to be thumbnailed.

---

### Post by ebe326 on 2008-01-09
It may just be the file size limit. Go to Edit>Preferences>Preview and increase the file size for thumbnails.

david

---

### Post by Fleece Flamingo on 2008-01-09
None of those worked ](*,)

---

### Post by rune0077 on 2008-01-09
What movieplayer do you have installed? Totem should be able to thumbnail videofiles by itself, as far as I know.

---

### Post by RomeReactor on 2008-01-09
Hi. From the terminal, run:
```
gconf-editor
```
there, go to 'Desktop->Gnome->Thumbnailers' and make sure the thumbnailers for the formats you want are enabled, such as "video@mpeg", "video@x-avi", "video@matroska", etc.

---

