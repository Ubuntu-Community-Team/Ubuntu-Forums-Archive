---
title: "Text overlay on kde?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by wirelessmonkey on 2006-11-07
This has probably been answered, but I'm not entirely sure how to ask the question and have had no luck searching the forums.

I want to display the contents of /var/log/messages as a transparent overlay on my KDE desktop. I want my normal background to stay there, and have the text appear on top. I don't want a shell there, I don't want to do any editing from the desktop background. I just want the text to appear, dynamically if possible, so I always know what's happening in /var/log/messages. Can anyone give me a hand?

wm

---

### Post by LadyDoor on 2006-11-07
See this thread! Something like this is useful if you use
KDE/Gnome/Fluxbox, etc.

[http://ubuntuforums.org/showthread.php?t=36811&highlight=devil+pie](http://ubuntuforums.org/showthread.php?t=36811&highlight=devil+pie)

The change you need to make would need to be putting your logger or
output program into the Eterm command line, so it would read like
this:

```

Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 200x60+80+40 --font-fx none -f white -e YourCommandNameHere

```

And that should hopefully do the trick.

---

