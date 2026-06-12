---
title: "Need help, Feisty beginner"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by kaxx on 2007-04-21
I'm trying to figure out why when I right click on an .exe file it won't pull up "Open with Wine Emulator" like it used to before I did the re-install upgrade to Feisty. When I open terminal, type wine and drag the .exe file into the terminal, all seems to go well (I haven't fully installed the program, yet).

I know this has been answered many times, but I did a search and can't find anything on this particular issue....

---

### Post by heimo on 2007-04-21
This is what I'd try:
[LIST=1]
[*]right click on the file
[*]select properties
[*]select open with tab
[*]select wine or if that's not available, add it through "+ add"
[*]close, right click on the file[/LIST]

---

### Post by kaxx on 2007-04-21
> **heimo said:**
> This is what I'd try:
[LIST=1]
[*]right click on the file
[*]select properties
[*]select open with tab
[*]select wine or if that's not available, add it through "+ add"
[*]close, right click on the file[/LIST]

Thanks, but unfortunately I tried that and Wine isn't in there.

---

### Post by heimo on 2007-04-21
Then use "custom command" at point 4. Correct path is probably /usr/bin/wine (please check that this file exists).

---

### Post by kaxx on 2007-04-21
There, that got it. Thanks for the help, how do I add wine to the applications menu?

---

### Post by heimo on 2007-04-21
> **kaxx said:**
> There, that got it. Thanks for the help, how do I add wine to the applications menu?

I think it should be there automatically when installed, but as you're missing it, try right-clicking on the "Applications", choose "Edit Menus" and see if it's unchecked. If it isn't listed, use "+ New Item" to add it.

---

### Post by kaxx on 2007-04-21
For some reason, it wasn't there automatically on this first time Install of Feisty but it was when I did the same steps in Edgy Eft. Or perhaps I've missed something. Maybe the program Automatix has something with my ease of installs on Edgy (can;t remember, I'm new and have installed Ubuntu 4 times)

Can anyone point me in the right direction for Automatix info, what exactly it does (all I know is it;s supposed to make Ubuntu easier to use somehow...)

---

