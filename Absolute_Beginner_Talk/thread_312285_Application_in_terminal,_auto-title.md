---
title: "Application in terminal, auto-title"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by disc on 2006-12-04
Is there a way to set the title for a Terminal upon opening it, without doing it manually or changing it's profile? I have a launcher for irssi on my panel, and I want it to set it's own title upon opening. Can anyone tell me how to do so?

---

### Post by disc on 2006-12-10
Or perhaps a way to have the terminal open in a profile that isn't the Default?

---

### Post by disc on 2006-12-10
Okay, so I did a little searching on how to have the terminal open into a non-Default profile. I found that you can do so with the command: 
```
gnome-terminal --window-with-profile=(profile name)
```
However, I still haven't figured out how to get it to open up an application with this method. If I try:
```
gnome-terminal --window-with-profile=IRSSI **irssi**

*or*

gnome-terminal **irssi** --window-with-profile=IRSSI
```
The terminal opens, then shuts. I played around with making a script, then executing it, but couldn't figure out how to do it that route. Any ideas?

---

### Post by 23meg on 2006-12-10
Use the -e option. ```
gnome-terminal -e=irssi --window-with-profile=IRSSI
```
[QUOTE=disc]I did a little searching on how to have the terminal open into a non-Default profile[/QUOTE]Did you look in the man page? Just wondering, since -e is on the very top and easy to see.

---

### Post by disc on 2006-12-10
> **23meg said:**
> Use the -e option. ```
gnome-terminal -e=irssi --window-with-profile=IRSSI
```
Did you look in the man page? Just wondering, since -e is on the very top and easy to see.

Thank you! Works like a charm. :)

---

### Post by 23meg on 2006-12-10
You're welcome. If you wanted to do this with a script, appending *read* to the end would keep the terminal open.

---

