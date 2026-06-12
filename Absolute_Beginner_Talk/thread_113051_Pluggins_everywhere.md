---
title: "Pluggins everywhere"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by aaalunchbox on 2006-01-05
here is the lowdown.

i got firefox 1.5 installed now.  The current plugin directory for firefox is at > ~/.mozilla/plugins

Now, anytime i install new plugins (like the backport java plugin for firefox) it dumps the plugins into > /usr/lib/mozilla-firefox/plugins

now i've heard of symlinking and i'm fairly sure about how it works.  However, i'm not sure how i can use it in this situation.  Any suggestions?

---

### Post by amohanty on 2006-01-05
Try:

> ln -s  /usr/lib/mozilla-firefox/plugins/plugin-name  ~/.mozilla/plugins/plugin-name

HTH

---

### Post by Sokraates on 2006-01-05
Creating a link is very simple. First of all, you can simply drag and drop a link from any file to any folder you have write-permission to (usually your home-folder).  At least with KDE you then get the option to copy, move or create a link. Gnome should be similar.

Another method is executing a command in a terminal:

```
ln -s /source/folder/file /target/folder/
```

"ln" is the command for creating a link. "-s" means, a symbolic link will be created.

---

### Post by aaalunchbox on 2006-01-09
well thank you very much for that.  I don't know what i was thiking to make it seem so hard.  :p  Plus, for some reason, i like using the terminal more then thru a gui.  Dunno why, maybe my mother potty trained me too soon.  :)

---

