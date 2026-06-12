---
title: "No Gnome Toolbar"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by BlackBoots on 2007-10-09
Today I was fooling around with compiz.  Installing all the little extras.  

I was having trouble getting the window decorations to show up.  After a few hours of searching and experimenting.  I finally got the max and min buttons to come back.  

Of course that wasn't enough for me I had to keep fooling around.  So i went through this walkthrough, [How exactly to get Compiz Fusion running with no knowledge of linux and no linux install]("http://puttabutta.blogspot.com/search/label/ubuntu")(have to scroll a ways to get to it), to get the latest version compiz and all the other extras.  

Anyways, after doing all that, my window decorations disappeared again.  I could not remember all the things that I had done to get them back. so i just restarted x(ctrl-alt-backspace)  And when everything loaded back up I had no bottom or top toolbar on the desktop.  Anyone have any ideas on how I would get it back.  Then I can start fighting again to get the window decorations in compiz.  

Thanks in advance.

Shawn

---

### Post by FuturePilot on 2007-10-09
Try putting this in a terminal
```
gnome-panel &
```

---

### Post by BlackBoots on 2007-10-09
Thanks for the quick reply.  

This is what I get when running that.

"I've detected a panel already running and will exit"

---

### Post by ronmarley1 on 2007-10-09
Try:
alt+F2
```
killall gnome-panel
```

---

### Post by BlackBoots on 2007-10-09
Well that was easy.  

Thanks

---

### Post by ronmarley1 on 2007-10-09
No worries.
Did you get your window decorator back?  For me, when I upgraded to Gutsy, I had issues with the GTK Window Decorator and went back to using Emerald.

---

### Post by BlackBoots on 2007-10-09
it is working in beryl but not compiz.  The decorations are there but it is not doing what it should.  No window wobbles ect.

---

### Post by ronmarley1 on 2007-10-09
Are you sure compiz is running?
Try:
alt+F2
```
compiz --replace
```

---

### Post by BlackBoots on 2007-10-09
I just decided to Upgrade to Gusty.  It's Still DLing, but from what i hear compiz is th edefault desktop.

---

