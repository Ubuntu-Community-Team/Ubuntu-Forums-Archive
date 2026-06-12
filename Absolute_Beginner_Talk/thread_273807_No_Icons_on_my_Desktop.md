---
title: "No Icons on my Desktop"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-10-08
Why can't I have any icons on my desktop?  When I try install a new applications and want to have access to it quickly like Sreem or Nvu, Ubuntu will not let me have it as an icon on my desktop.  Not only those programs but if I download something on to my desktop it isn't there.  Instead I have to go to my desktop folder to get it.  What do I have to do to get icons on my desktop?](*,)

---

### Post by CatKiller on 2006-10-08
Have you installed XGL/Compiz? I've read that that can mess up your desktop icons if it isn't configured correctly.

When it's all configured properly, you can drag-and-drop from the menu to the desktop to make a launcher.

---

### Post by jordanmthomas on 2006-10-08
Press Alt + F2
type
```
gconf-editor /apps/nautilus/preferences
```
Make sure "show desktop" is checked on the right

---

### Post by NeoGreen on 2006-10-11
Wow, thanks.  I didn't install anything that might have caused my desktop to not show.  Anything else that might cause that to happen?

---

### Post by jordanmthomas on 2006-10-11
I can't think of anything except changing it yourself or via some program...I dunno how it got that way, but you were able to fix it, correct?

---

### Post by NeoGreen on 2006-10-12
Yeah, your solution worked.  Thanks for the information.

---

