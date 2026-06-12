---
title: "Using Xubuntu, orange boot up screen stayed."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-17
I restarted my computer and the orange screen that comes up before XFCE loads stayed on. I know I could probably just put my old background over it, but I would like to know why this happened. I installed frostwire, then I installed some games from Add/Remove programs.

[COLOR="Red"]**Edit:**[/COLOR] nvm, It wouldn't let me right click on the desktop so I didn't view the desktop settings, but after accessing desktop settings the other way, I could clearly see that "allow XFCE to manage desktop" was unchecked, I checked and it went back to normal. I'm not going to hit solved yet, because I'm still curious as to why this happened and welcome enlightmentment. Thank you.

---

### Post by Fate Reconciled on 2008-03-17
I had the same problem with Xubuntu. What happens is when Xfce starts, it's not set to manage your desktop as default. What happens as a result of this is...

Tada! The GNOME environment starts up instead!

Checking "Allow XFCE to manage desktop" does indeed solve this problem as far as I know, since it's worked fine for me ever since.

Hopes this gives you a little peace of mind...

---

### Post by whoscheesemine on 2008-03-17
Well, the thing is that I had it checked before I restarted my computer.

---

### Post by Fate Reconciled on 2008-03-17
Make sure Xfce doesn't save the session.

---

