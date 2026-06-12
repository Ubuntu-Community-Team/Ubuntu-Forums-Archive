---
title: "How do you change application to open specific filetype."
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2007-01-10
Hi. I was wondering how do I change the default application to open a specific filetype. In my case I want to use VLC instead of Totem for video files, and amarok instead of totem for audio files. How would I do this?

---

### Post by Nakajoe on 2007-01-10
Easiest way is to right click the file, properties, open with, and then select (add as necessary) what you want to use.

---

### Post by ComplexNumber on 2007-01-10
> **jincast90 said:**
> Hi. I was wondering how do I change the default application to open a specific filetype. In my case I want to use VLC instead of Totem for video files, and amarok instead of totem for audio files. How would I do this?
  if you want the default changed, go to main menu -> system - preferences -> removable drives and media. then click on the multimedia tab.

---

### Post by jincast90 on 2007-01-12
> **ComplexNumber said:**
> if you want the default changed, go to main menu -> system - preferences -> removable drives and media. then click on the multimedia tab.

Oh.. That is nice too. But what I am looking for is to for example, when double clicking on a .avi file on the Desktop then have the .avi file opened in VLC media player by default instead of Totem.

---

### Post by jincast90 on 2007-01-13
Bump.

---

### Post by tweedledee on 2007-01-13
> **jincast90 said:**
> Bump.

Right-click on the file, select Properties -> Open With, and make sure whichever program you want to always open with by default is the one with the radio button selected.  But since Linux does not recognize files by extension, .avi files that aren't actually the same type will need to be separately (I occasionally run into this, as some extensions like .avi actually encompass a variety of mime types).

---

### Post by hpp3 on 2007-02-06
If you're in for serious mime-type editing, dig around /usr/share/mime-info and /usr/share/applications/defaults.list

---

