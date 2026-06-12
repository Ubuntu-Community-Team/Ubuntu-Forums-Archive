---
title: "Add a shortcut to 'Filesystem' on the desktop"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-18
Is it possible to add a shortcut to **Filesystem** on the desktop? I used to like the fact that Fedora had such a shortcut right there on the desktop - but Ubuntu won't let me create one.... :(

---

### Post by Yopo on 2006-12-18
$ gconf-editor (type gconf-editor in a terminal).
apps->nautilus->desktop.
Check computer_icon_visible, home_icon_visible and trash_icon_visible.

---

### Post by dbbolton on 2006-12-18
you could just create a new launcher, and on the command line type
```

nautilus '/'
```

---

### Post by John E on 2006-12-18
Slightly off topic - but a few weeks ago I read something about a menu editor - that allows you to add & remove things from the standard menus.  In fact I even used it but I can't remember how to launch it. Can anyone remind me please?

---

### Post by Izobalax on 2006-12-18
> **John E said:**
> Is it possible to add a shortcut to **Filesystem** on the desktop? I used to like the fact that Fedora had such a shortcut right there on the desktop - but Ubuntu won't let me create one.... :(
Hmmm ... I can do this fine ...

Go to Places > Computer, in the window that opens up, drag the 'Filesystem' icon onto your desktop. Voila!

---

### Post by John E on 2006-12-18
Oh, how stupid of me... :redface: I was trying to create a link. I knew it would be obvious!!

---

### Post by Izobalax on 2006-12-18
> **John E said:**
> Oh, how stupid of me... :redface: I was trying to create a link. I knew it would be obvious!!
Hah! No worries.

---

### Post by John E on 2006-12-18
EEK...! I spoke too soon!!

Ever since I placed that FileSystem icon on my desktop I've been unable to boot up. My system stops at 'Mounting the root file system'.

I can't boot up either normally or in Recovery mode. If I booted up from the live CD, would it be possible to undo that change?

---

### Post by Yopo on 2006-12-19
I think it could be possible. Obviously you first need to mount your root partition, do you know how to do that? Otherwise I can help you with that to start with, let me know how you faired till now...

---

### Post by John E on 2006-12-19
Thanks for the offer of help but I ended up restoring a recent backup.

---

### Post by whoismilan on 2006-12-19
[QUOTE=John E]Slightly off topic - but a few weeks ago I read something about a menu editor - that allows you to add & remove things from the standard menus. In fact I even used it but I can't remember how to launch it. Can anyone remind me please?[/QUOTE]
System > Preferences > Menu Layout ;)

---

