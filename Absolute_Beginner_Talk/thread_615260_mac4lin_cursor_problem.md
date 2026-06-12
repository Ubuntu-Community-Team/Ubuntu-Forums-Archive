---
title: "mac4lin cursor problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by limac on 2007-11-16
Hi,

Ok, so I installed Mac4Lin and it's running fine. But when i select the mac os x cursor (pointer) theme and then restart the computer it's not working, the mac os cursor is not appearing in the desktop window, but when my mouse is over the firefox window, the os x cursor is appearing in the firefox window. So how exactly can I get that theme to work on the desktop?

---

### Post by Frak on 2007-11-16
How did you get the mouse theme to work in the first place? I can't get it to work with Gnome 2.20.

---

### Post by limac on 2007-11-16
go to appearance, then click install, navigate to where you untarred your mac4lin themes. there click on Cursors and then click open, that sort of changes the icon, but then logout and relogin and then go to appearance and click install and again install the icon theme for Gnome 2.20... and then finally in your appearance window click on customize, go to pointers select mac os x pointer, logout, relogin, and it SHOULD work, i don't know why it isn't in my case though...

---

### Post by Frak on 2007-11-16
thanks, have you logged out and logged back in yet?

---

### Post by limac on 2007-11-16
yeah but somehow it not working

---

### Post by limac on 2007-11-17
any help would be appreciated

---

### Post by limac on 2007-11-17
yo anyone!

---

### Post by lakerssuperman on 2007-11-17
Hello.  I have the same problem.  When I login I see the black OSX cursor theme but then it changes right back to the white default pointer.  My guess is that it is being set and then overridden somehow.  I'n not sure how to fix it yet, but if I find anything I'll be sure to post it.

---

### Post by coman on 2007-12-11
hey Limac, i was having the exact same problem as you and found the solution in another post.  It seems that there is some sort of issue with emerald being overridden by the regular cursor app.  All you have to do is use synaptic to uninstall emerald, restart your computer, reinstall emerald, and then make sure theme and cursor settings you want are applied, and then restart once again.  This solved all problems for me and a few others, hope this helps

---

### Post by nashkrammer on 2008-01-05
cursor theme is reset to default by emerald. i disabled emerald by running (metacity --replace) then cursors work fine but compiz effects r lost. the only option i think is to uninstall emerald...

---

