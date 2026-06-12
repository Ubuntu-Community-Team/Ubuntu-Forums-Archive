---
title: "[SOLVED] How to find out what programs menu buttons are running"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by mike_something on 2007-11-08
Hi, just installed xubuntu 7.10 and have a couple of questions I can't find answers to.

1. How do you find out what the items in the Applications menu actually run? They seem to launch no matter what mouse button I press.  The menu config just shows a link to an external menu (which I can't seem to figure out how to find or edit).

2. Is this normal behaviour or have I done something wrong?

Thanks,
Mike

---

### Post by yabbadabbadont on 2007-11-08
Edit: I completely missed the fact that it was xubuntu...  :oops:

---

### Post by mike_something on 2007-11-08
Thanks for the reply, but my problem is what happens when I right-click.
1) On applications button => Can add item - but new launcher is blank
2) On sub-menu Heading => No reponse
3) On sub-menu Item => Program automatically launches (same with middle click)

Cheers,
Mike

---

### Post by mivo on 2007-11-08
> **mike_something said:**
> 1. How do you find out what the items in the Applications menu actually run?

Go to *System -> Preferences -> Main Menu*, right-click on the program and select "properties".

---

### Post by mike_something on 2007-11-08
Hmm,
This might be a xubuntu vx Ubuntu thing but I don't have a System -> Preferences -> Main Menu option.

I've got 
Applications -> System -> ( and then nothing to do with Preferences or Menus)

or

Applications -> Settings -> Menu Editor
--- which pulls up a Menu editing window, but the "system menu" entry is highlighted in green and double clicking or selecting it in various ways just seems to open another small window that is titled "Edit External Menu Entry"  -- but I can't actually seem to use this window to edit it in any way.

or

Applications -> Settings -> Settings Manager
--- which has a whole 12 icons - none of which I can find that help

Thanks,
Mike

---

### Post by mivo on 2007-11-08
I have Xubuntu on an older box, but it's in a different location so I can only check in the morning. You can also look in **/usr/share/applications** in your file manager and right-click the items in there for details (this *should* work in Xubuntu, too).

---

### Post by mike_something on 2007-11-08
look in /usr/share/applications

That did the trick,
Thanks,
Mike

---

