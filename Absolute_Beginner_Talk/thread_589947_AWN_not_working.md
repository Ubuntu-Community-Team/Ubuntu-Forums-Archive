---
title: "AWN not working?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by gc091 on 2007-10-24
Tried installing the AWN dock in Gutsy by following the instructions elsewhere in the forums. When i go to system>preferences, there is an option for "AWN Manager", but when i click on it nothing happens. Tried restarting etc. Any Ideas? Help much appreciated.

---

### Post by angkor on 2007-10-24
> **gc091 said:**
> Tried installing the AWN dock in Gutsy by following the instructions elsewhere in the forums. When i go to system>preferences, there is an option for "AWN Manager", but when i click on it nothing happens. Tried restarting etc. Any Ideas? Help much appreciated.

Try starting it from the terminal, maybe you get a useful error message:

```
avant-window-navigator
```

---

### Post by gc091 on 2007-10-24
haha that simple! thanks. how do i make it start every time i logon?

---

### Post by johnnybirdman on 2007-10-24
> **gc091 said:**
> haha that simple! thanks. how do i make it start every time i logon?

To go at startup I would think you add that command to the sessions.. make sure it's enabled.

What guide did you use to get it installed?

J

---

### Post by gc091 on 2007-10-24
I used [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981) to install. i've got it all working now tho. thanks guys

---

### Post by Inxsible on 2007-10-24
> **gc091 said:**
> Tried installing the AWN dock in Gutsy by following the instructions elsewhere in the forums. When i go to system>preferences, there is an option for "AWN Manager", but when i click on it nothing happens. Tried restarting etc. Any Ideas? Help much appreciated.
The reason its not starting from the System --> Preferences --> Awn Manager is that you must have created a launcher without an icon. I have seen that happen to me and it just wouldn't bring up the manager after that. Delete the .awn folders in your home directory and then try. 

That should work too

---

### Post by MarimaX on 2008-01-09
I tried all this and re-followed the same guide.  I still can't get it to show up on the desktop.

---

