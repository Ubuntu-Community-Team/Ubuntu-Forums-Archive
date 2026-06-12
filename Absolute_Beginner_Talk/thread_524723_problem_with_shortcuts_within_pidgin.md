---
title: "problem with shortcuts within pidgin"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by skynix on 2007-08-13
Okay, I was using gaim earlier this morning, and the laptop slipped off my lap and rather than let it fall I grabbed onto it and by some strange coincidence whatever keys my grasping hand hit, they changed the keyboard shortcut for initiating chats in msn to just the letter o. This is something of a problem, because I have become used to using the letter o in conversations.

I've googled for a straight hour now and I can't find anywhere that tells you how to reset or change keyboard shortcuts within gaim.

So, uh, help please? 

(also I attempted to upgrade to pidgin to see if it would erase this, but apparently the transition package carried over my keyboard shortcuts along with the logs, so...yeah...)

---

### Post by nvrpunk on 2007-08-13
open up a terminal, it should bring you into your home directory.

type "rm -r .gaim" minus the quotes.

reopen gaim.

hope that works for ya.

---

### Post by abehrens on 2008-01-08
You don't have to remove the .gaim [Gaim] or .purple [Pidgin] directory.

You can hover over the affected menu item and press the key[s] that you want instead of the currrent shortcut, and that will redefine it.

If the ability to change menu shortcuts has been disabled, you can edit the shortcut file directly with your favorite editor. (Quit out of Gaim/Pidgin first). The shortcut file is in your home directory, called *.purple/accels* , and you can just comment out the offending line to restore the default setting.

---

