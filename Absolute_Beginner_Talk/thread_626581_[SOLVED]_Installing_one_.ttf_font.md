---
title: "[SOLVED] Installing one .ttf font"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-11-29
I have one font that I downloaded that I need to use to make a web site graphic. It is a .ttf font, and I would like to know how to install just this one font so I can use it in GIMP.

I have tried dragging it into the fonts folder, and that didn't work :(

---

### Post by mcduck on 2007-11-29
Create a directory called .fonts inside your home dir, and put the .ttf file there. You may need to log out and back again before all programs recognize the new font.

---

### Post by Akuma Shiro on 2007-11-29
How do I go about creating a directory? I doubt it's the same thing as creating a new folder...

---

### Post by mcduck on 2007-11-29
> **Akuma Shiro said:**
> How do I go about creating a directory? I doubt it's the same thing as creating a new folder...
It is the same thing. 'Folder' is just a new name for directory..

It might also help to know that directories and files with a dot in the beginning of the name are hidden, so the directory will disappear after you have created it. You can show hidden files and directories in the file manager by pressing Ctrl-h.

---

### Post by timcredible on 2007-11-29
to install new fonts, do Places->Home Folder, then Go->Location and type in fonts:/// and then drag your new font file into that directory.

---

### Post by forestpixie on 2007-11-29
might need to update as well 

```
sudo fc-cache -f
```

---

