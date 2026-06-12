---
title: "[SOLVED] wallpapers!!"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-09-02
A very simple question! i have a folder with some 450 odd images which i use as wallpapers!!!! is there any way i can add all of them to the "Change Desktop Background" dialog...i am tired of adding them one by one!

---

### Post by jordanmthomas on 2007-09-02
Select them all in a file browser window and drag them onto the change background window.

---

### Post by badguyanil on 2007-09-02
Thanks mate!

---

### Post by sstusick on 2007-09-02
Is there a particular folder/directory where the default wallpaper is stored?

---

### Post by jordanmthomas on 2007-09-02
> **sstusick said:**
> Is there a particular folder/directory where the default wallpaper is stored?

Yes, it is /usr/share/wallpaper if I'm not mistaken (on an OS X box right now, so I can't confirm)

However, adding wallpapers here shouldn't make them automatically show up I don't think.

---

### Post by Genecks on 2007-09-02
Here's another tool to play with... gotta do with gconf-editor.

> gconftool-2 --type string --set /desktop/gnome/background/picture_filename $HOME/wallpapers/wallpaper.jpg

I believe if you put things in the share folder, you've got to change their permissions.

---

### Post by jordanmthomas on 2007-09-02
[offtopic]
Is it just me, or is gconf scarily close to the idea of the Windows registry?  *shudder*
[/offtopic]

---

