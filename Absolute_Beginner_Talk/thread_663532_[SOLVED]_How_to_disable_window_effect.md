---
title: "[SOLVED] How to disable window effect"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by bitra on 2008-01-10
I want more speed for my Ubuntu, so I changed the desktop visual effect to "none". But every time I minimize a window, the tail effect of the window is still active. Is it possible to disable this? In what way?

Thanks.

---

### Post by Mr Fredrick on 2008-01-10
See this thread:

[http://ubuntuforums.org/showthread.php?t=662926](http://ubuntuforums.org/showthread.php?t=662926)

It may help, although it may not turn off ALL effects.

---

### Post by FriedChips on 2008-01-10
you could just uninstall compiz completely, but this may or may not be a compiz effect... try top or htop. I prefer htop to check running processes
```
sudo apt-get install htop
```
and see if you can find compiz in there anywhere. Best to sort by user though cuz thats a long list. You can remove compiz with:
```
sudo apt-get remove compiz
```

---

### Post by mcduck on 2008-01-10
> **bitra said:**
> I want more speed for my Ubuntu, so I changed the desktop visual effect to "none". But every time I minimize a window, the tail effect of the window is still active. Is it possible to disable this? In what way?

Thanks.

do you mean the ugly wireframe animation? That's a feature of Gnome's default window manager, Metacity. It can be disabled from Configuration Editor:

1. Press Alt-F2 and run 'gconf-editor' to start the Configuration Editor
2. Browse to apps/metacity/general
3. Enable the 'reduced_resources'-key.

Enabling reduced_resources will also hide window contents when moving/resizing. But enabling accessibility support will solve this problem:

4. Browse to desktop/gnome/interface
5. Enable the 'Accessibility'-key.

To further increase performance, also disable the 'enable_animations'-key in the same place.

---

### Post by bitra on 2008-01-11
> **mcduck said:**
> do you mean the ugly wireframe animation?

That's it. I want to remove that thing.

> **mcduck said:**
> That's a feature of Gnome's default window manager, Metacity. It can be disabled from Configuration Editor:

1. Press Alt-F2 and run 'gconf-editor' to start the Configuration Editor
2. Browse to apps/metacity/general
3. Enable the 'reduced_resources'-key.

Enabling reduced_resources will also hide window contents when moving/resizing. But enabling accessibility support will solve this problem:

4. Browse to desktop/gnome/interface
5. Enable the 'Accessibility'-key.

To further increase performance, also disable the 'enable_animations'-key in the same place.

It works! Now the wireframe animation is disabled, and I get a small burst of speed. :) Thanks **mcduck** !

---

