---
title: "Clearing Run Application List"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Epperly on 2007-01-15
Anyone know how to do this? Thanks!

---

### Post by ardchoille42 on 2007-01-15
What run applications list? Are you using gnome? If so, which list are you referring to? The menus? Recently Used files?

---

### Post by Epperly on 2007-01-15
In gnome... I think OEM is ALT+F4? I have mine set to ALT+R though
it's just called "Run Application"... a little box like Window's run

---

### Post by ardchoille42 on 2007-01-15
Oh, ok, I"m with you now. In the default Ubuntu Dapper install from the alternate CD, it's ALT+F2. Open the file ~/.gconf/apps/gnome-settings/gnome-panel/%gconf.xml in a text editor and have a look at it. I did ALT+F2, typed in "nautilus /usr/share/doc/zip" and pressed run.. I did that so it would save the "nautilus /usr/share/doc/zip" entry and then I searched (in a terminal) for that entry with:

grep -r "nautilus /usr/share/doc/zip" ~/.gconf

and it returned that file. Have a look at it. You may be able to delete or move ~/.gconf/apps/gnome-settings/gnome-panel/%gconf.xml and the Run Applications entries will be empty the next time you log into gnome.

---

### Post by Epperly on 2007-01-15
Thanks! I just deleted it and then logged out and back in and it worked.
:D

---

### Post by ardchoille42 on 2007-01-15
> **Epperly said:**
> Thanks! I just deleted it and then logged out and back in and it worked.
:D

Well, if that's the case, you can keep gnome from creating that list in the future if you know you don't want it.

Open a term, and do:

```

cd ~/.gconf/apps/gnome-settings/gnome-panel && ln -s /dev/null %gconf.xml

```

That will make it so that all new items, that would normally go to that list, now go to /dev/null and the list is never again created until you remove the symlink..

---

### Post by xpod on 2007-01-15
I was wondering the exact same thing myself yesterday.
I`d had a couple of dodgy entries in the run menu compliments of my dodgy typing.

Not now:D

---

