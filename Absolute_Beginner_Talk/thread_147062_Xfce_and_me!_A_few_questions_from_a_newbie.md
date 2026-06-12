---
title: "Xfce and me! A few questions from a newbie"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-03-19
Okay, I ran a server install of Ubuntu, got into the sources.list and uncommented, updated, installed xubuntu-desktop, updated again, and it works.  Xfce works great, and I gotta say that Ubuntu rules.

But, my question is about desktop icons. I'd like to set up a "Computer" icon, that holds all the folders and stuff, like the My Computer thing in Windows. I know I can just load File manager, but is there a way to get it on the desktop? I got into the habbit of My Computer, and still find it to be handy. So if anyone could help, it would me much appreciated. Thank you! =D

---

### Post by taurus on 2006-03-19
To create icons on your desktop, you need idesk!!!

---

### Post by aysiu on 2006-03-19
Alt-F2 ```
nautilus
``` and make sure in XFCE Settings you save sessions on logout.

---

### Post by blackrim on 2006-03-19
i have, i think, an inverse problem to the one mentioned above...
i seem to lose my right clicking menu abilities when I run something like f-spot in xfce. i assume it has something to do with some nautilis library starting up when f-spot starts (although I don't have nautilus installed)
any thoughts?

---

### Post by 5-HT on 2006-03-19
[quote=blackrim]i have, i think, an inverse problem to the one mentioned above...
i seem to lose my right clicking menu abilities when I run something like f-spot in xfce. i assume it has something to do with some nautilis library starting up when f-spot starts (although I don't have nautilus installed)
any thoughts?[/quote] 
What about starting up 'xfdesktop' when that happens?
It's responsible for drawing the desktop and the right & middle click menus in XFCE.

As to why that's going on...not sure, and I don't have f-spot installed myself.
I do know that nautilus does take over the desktop and to get around this you can call it up with 'nautilus --no-desktop'...but you mentioned that you don't even have nautilus installed.

Until the problem gets sorted out, calling 'xfdesktop' after you're done with f-spot may help.

---

