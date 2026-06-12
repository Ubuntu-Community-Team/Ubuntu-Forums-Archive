---
title: "Why can't I create desktop shortcuts?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Quillz on 2007-01-02
This is going to sound really stupid, but I want to create a desktop shortcut to the "home" directory, or the "Computer" directory. In both cases, if I try to drag the icons (or copies of the icons) to the desktop, I get an error message. Note that I also want "Trash" to appear on the desktop, but can't figure out how. In many desktop screenshots, I've seen the Computer and Trash icons on the desktop, so I know it's possible.

---

### Post by benuski on 2007-01-02
If you want just normal programs to be on the desktop, just right click and choose "Create Launcher".  For Computer or Home or things like that, type in "gconf-editor" into the terminal, and then go to "Apps"->"Nautilus"->"Desktop", and then click off the boxes you want to be visible.

---

### Post by charles.g.moore on 2007-01-02
If I understand you right in order to create a "shortcut" you could right click > create launcher  > then call nautilus for your filesystem

As  far as the trash goes im not too sure...

---

### Post by jblebrun on 2007-01-02
> **Quillz said:**
> This is going to sound really stupid, but I want to create a desktop shortcut to the "home" directory, or the "Computer" directory. In both cases, if I try to drag the icons (or copies of the icons) to the desktop, I get an error message. Note that I also want "Trash" to appear on the desktop, but can't figure out how. In many desktop screenshots, I've seen the Computer and Trash icons on the desktop, so I know it's possible.

When explaining a problem, you should try to be as descriptive as possible. Saying "it didn't work" or "I got an error message" makes it difficult for people to help you. You should explain exactly what you did (from where were you dragging icons, which desktop environment are you using) and exactly what happened (what did the error message say, exactly?) 

The more details, the more likely someone will be able to help you quickly and efficiently!

---

### Post by 3rdalbum on 2007-01-02
Press Alt-F2, type "gconf-editor" and press OK.

Now go apps > nautilus > desktop and tick the "trash_icon_visible" and "home_icon_visible" boxes. The change should take effect immediately.

---

### Post by Quillz on 2007-01-02
> **benuski said:**
> If you want just normal programs to be on the desktop, just right click and choose "Create Launcher".  For Computer or Home or things like that, type in "gconf-editor" into the terminal, and then go to "Apps"->"Nautilus"->"Desktop", and then click off the boxes you want to be visible.
Thanks so much! That did exactly what I was looking for. :-D

> **jblebrun said:**
> When explaining a problem, you should try to be as descriptive as possible. Saying "it didn't work" or "I got an error message" makes it difficult for people to help you. You should explain exactly what you did (from where were you dragging icons, which desktop environment are you using) and exactly what happened (what did the error message say, exactly?) 

The more details, the more likely someone will be able to help you quickly and efficiently!
Thank you for the suggestion. I'll try to be more descriptive in the future.

---

