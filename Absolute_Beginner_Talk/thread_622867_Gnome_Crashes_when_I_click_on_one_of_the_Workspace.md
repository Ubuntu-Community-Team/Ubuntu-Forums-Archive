---
title: "Gnome Crashes when I click on one of the Workspace switcher Icons ..."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-25
When I click on one of the Workspace Switcher Icons in the lower right panel, all my Desktop icons disappear, and both the top application panel and the bottom windows switcher panel disappears.

The only way I can recover is via Ctrl + Alt + Backspace.

I am using Compiz effects.

Anyone else experience this?

Carl

---

### Post by cwmoser on 2007-11-26
Another observation regarding this.... Once I press Ctrl + Alt + Backspace and relogin, I can select the Workspace icons and they work as expected.  The Gnome Crash occurs during the first logon after power up.

Carl

---

### Post by DutyDuty on 2007-11-26
I'm not trying to be rude, but if you're using compiz, do you need to use those?

---

### Post by Slayta on 2008-01-04
im having the same problem. only by restarting does it work fine. I'm also using Desktop Effects.  if that has any relevancy.

---

### Post by njparton on 2008-01-04
It's probably a compiz and metacity conflict.

Get rid of compiz and then reconfigure gnome to use metacity as the default window manager:

```

gconf-editor

```

it's one of the options in there but can't remember specifically where off the top of my head.  Search the forum, there's a thread that deals with it somewhere here.

If you really "need" compiz then you'll have to live with the problem though. It's just a gimick in my book.

---

