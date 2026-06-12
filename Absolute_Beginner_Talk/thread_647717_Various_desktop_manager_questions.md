---
title: "Various desktop manager questions"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-22
1. Most applications are "designed" to fit well into Gnome or KDE. On Xfce, are one of these preffered? In other words, are Gnome and Xfce somehow more compatible than KDE and Xfce? I have no reason to think so, but I dream up some weird questions...

2. Is it a better idea to have all Gnome or all KDE apps rather than a mix-and-match? And part b: If I have one KDE app and 100 Gnome apps, is that any different performance wise than 51 Gnome and 50 KDE? I'm guessing no, because the libraries are already loaded.

I thought I had more questions. I'm sure I'll think of them and post them soon.

---

### Post by LaRoza on 2007-12-22
> **EmosSuck777 said:**
> 1. Most applications are "designed" to fit well into Gnome or KDE. On Xfce, are one of these preffered? In other words, are Gnome and Xfce somehow more compatible than KDE and Xfce? I have no reason to think so, but I dream up some weird questions...

2. Is it a better idea to have all Gnome or all KDE apps rather than a mix-and-match? And part b: If I have one KDE app and 100 Gnome apps, is that any different performance wise than 51 Gnome and 50 KDE? I'm guessing no, because the libraries are already loaded.


0. Xfce uses GTK so GNOME apps work on it well, but you can use any you want.

1. It doesn't matter. I use a mix. Ubuntu comes with the GTK libraries, but when you install a KDE app, the libraries are added. They may be slightly slower to start, but that is not really an issue. They run just fine.

---

### Post by Pogeymanz on 2007-12-22
Ooh! Thought of another one. Is there a simple way of renaming the desktop icons? If it's a really long process, then I don't care enough.

I just want to name the File System icon "The Machine" and silly stuff like that.

---

### Post by LaRoza on 2007-12-22
> **EmosSuck777 said:**
> Ooh! Thought of another one. Is there a simple way of renaming the desktop icons? If it's a really long process, then I don't care enough.

I just want to name the File System icon "The Machine" and silly stuff like that.

Rght click, select properties, rename.

Is this the icon on the desktop? That is how you do it. To get the icon on the desktop: ```
gconf-editor
``` and it is under Apps->Nautilus->Desktop

---

### Post by Pogeymanz on 2007-12-22
When I do that, the rename option is grayed out. Is there a way to do it from the Terminal so I can use the sudo command?

---

### Post by LaRoza on 2007-12-22
> **EmosSuck777 said:**
> When I do that, the rename option is grayed out. Is there a way to do it from the Terminal so I can use the sudo command?

I edited my post. I thought you wanted the desktop Icons renamed. I don't know about the menus.

The option should be there, I didn't have any trouble.

---

### Post by kellemes on 2007-12-22
> **EmosSuck777 said:**
> Is it a better idea to have all Gnome or all KDE apps rather than a mix-and-match? And part b: If I have one KDE app and 100 Gnome apps, is that any different performance wise than 51 Gnome and 50 KDE? I'm guessing no, because the libraries are already loaded.

I thought I had more questions. I'm sure I'll think of them and post them soon.

You better create seperate threads for seperate questions.. this makes it easier for others in search of answers.

Anyway.. I mix KDE and GTK apps.
For me it's all about using the app that's best for the task. I don't care how it looks or matches the environment as long as it works.
Differences in performance there are between apps. But as long as you don't notice there is no problem right?

---

