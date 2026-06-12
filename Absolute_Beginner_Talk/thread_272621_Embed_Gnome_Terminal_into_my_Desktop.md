---
title: "Embed Gnome Terminal into my Desktop?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Abstract on 2006-10-06
I have been on some websites and I have seen people with a Terminal on their Desktop. E.g. it is there when they login, and is above the wallpaper. It doesn't have the window manager stuff, it is just like it is typing onto the desktop.

Does anyone know how to get this?

---

### Post by Anonii on 2006-10-06
> **Abstract said:**
> I have been on some websites and I have seen people with a Terminal on their Desktop. E.g. it is there when they login, and is above the wallpaper. It doesn't have the window manager stuff, it is just like it is typing onto the desktop.

Does anyone know how to get this?
[http://www.ubuntuforums.org/showthread.php?t=81727](http://www.ubuntuforums.org/showthread.php?t=81727)

>:3

---

### Post by Abstract on 2006-10-06
That doesn't seem to be working for me..

```
loser@box:~$ alltray -x -st -g +777+24 gnome-terminal\ --window-with-profile=tterm

** ERROR **: file gnome_theme.c: line 194 (parse_theme): assertion failed: (theme_name)
aborting...
Aborted

```

---

### Post by BackInTimeMan on 2006-10-07
> **Abstract said:**
> That doesn't seem to be working for me..

```
loser@box:~$ alltray -x -st -g +777+24 gnome-terminal\ --window-with-profile=tterm

** ERROR **: file gnome_theme.c: line 194 (parse_theme): assertion failed: (theme_name)
aborting...
Aborted

```

Hi,

After making a new profile (trans) in the terminal, this is the command I put in a launcher and it works just fine:

```
alltray -x -g  +188+177 "gnome-terminal --window-with-profile=trans"
```

---

### Post by bobosity on 2006-10-09
Run a terminal and then right click on the face of it.
Choose 'edit current profile' 
Select 'effects'
Make it transparent

Is this what you are looking for?

---

