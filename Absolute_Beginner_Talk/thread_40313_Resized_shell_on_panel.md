---
title: "Resized shell on panel?"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by Musagetes on 2005-06-08
Hey, all.

I'm hoping someone knows if there's a trick to fixing the size of my shell (gnome-terminal) when I click on the icon on my panel. Currently it's way too big and just annoying, and it's even more annoying that I have to resize it to make the window smaller every single time I need to run a couple of commands.

So, is it possible to add some parameters to the launch command so that it will be smaller once opened?

Thanks in advance!

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=Musagetes]Hey, all.

I'm hoping someone knows if there's a trick to fixing the size of my shell (gnome-terminal) when I click on the icon on my panel. Currently it's way too big and just annoying, and it's even more annoying that I have to resize it to make the window smaller every single time I need to run a couple of commands.

So, is it possible to add some parameters to the launch command so that it will be smaller once opened?

Thanks in advance![/QUOTE]
 Right-click on the icon, select "properties". In "command" filed, you should have "gnome-terminal". Change it to 
```

gnome-terminal --geometry 60x20

```
or replace 60 by number of columns and 20 by the number of lines you like. 
Note: there are two dashes in front of "geometry", not one.

---

