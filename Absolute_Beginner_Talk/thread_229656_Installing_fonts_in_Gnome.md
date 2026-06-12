---
title: "Installing fonts in Gnome???"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-08-04
How can you install fonts in Gnome? 

I know that in KDE you just go to the corresponding control panel and just drag an drop them in there. This is VERY convenient for installing all your Windows fonts in linux - if you have Windows on another partition you can just drag and drop all the fonts from the Windows/Fonts folder.

Is there a way to do that in Gnome?

---

### Post by Jagot on 2006-08-04
Open a Nautilus window and hit ctrl+L and in the address bar type fonts:/// - you should be able to drag font's there.

Failing that, the method I use is to put them in the usr/share/fonts/ directory using Terminal:

```
sudo mv ~/Desktop/My\ Fonts /usr/share/fonts/truetype/
sudo fc-cache -f -v
```

---

