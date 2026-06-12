---
title: "[SOLVED] Want Icons not text shown on pdf's etc"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by billmik on 2008-02-11
Is there a way to set gutsy to show icons for pdf's,  jpegs, and text files instead of previewing them (actual text and picture is shown instead)?

---

### Post by aeiah on 2008-02-11
im not on my ubuntu machine right now, but i think there is a setting in gconf-settings for previewing text

---

### Post by LowSky on 2008-02-11
in termial type gconf-settings

go to apps>nuatilus---> somewhere in there..im also away form my ubuntu machine

---

### Post by billmik on 2008-02-11
> **aeiah said:**
> im not on my ubuntu machine right now, but i think there is a setting in gconf-settings for previewing text
When i type in gconf-settings i get 
bash: gconf-settings: command not found

---

### Post by y-lee on 2008-02-11
The  command is

```
gconf-editor
```

Also if it is installed it should be found in your menu somewhere for me it is under system tools. If it is not installed you can find it in Synaptic

```
/desktop/gnome/thumbnailers/applications@pdf
```

is the setting you wish to change. uncheck** enable**

---

### Post by asmoore82 on 2008-02-11
and to simply turn off thumbnail previews completely,
Open "System -> Preferences -> File Management"
Click the last tab, "Preview"
and change all of the "Local Files Only" to "Never"

---

### Post by billmik on 2008-02-11
> **asmoore82 said:**
> and to simply turn off thumbnail previews completely,
Open "System -> Preferences -> File Management"
Click the last tab, "Preview"
and change all of the "Local Files Only" to "Never"
 i dont have file management under Open "System -> Preferences -> File Management" How do i get it i looked in synaptic dont see it

---

### Post by y-lee on 2008-02-11
> **billmik said:**
> i dont have file management under Open "System -> Preferences -> File Management" How do i get it i looked in synaptic dont see it

you can open the Alcarte Menu editor and check to see if you have it and it is just unchecked. I think it is comes with gnome.

---

### Post by billmik on 2008-02-11
> **y-lee said:**
> you can open the Alcarte Menu editor and check to see if you have it and it is just unchecked. I think it is comes with gnome.

That did it! thanks y-lee I went under system> preferences> Main Menu and inside there it was un checked. So after i checked it and i ran the file management i got it the way i wanted. Thanks

---

