---
title: "Window Title"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-03-31
For some reason my title bar is huge at the top of my screen, I dont know why it is like this.  If I restart sometimes it will go back to normal but other times it wont.  I went to System>preferences>apperance>font tab and changed the window title font to 1 and then it looks normal but when i restart then the title is to small to see. and I have to change it back to 10 just so that I can see...

I attached a screen shot so that you can see what i mean about the size of the title bar.

---

### Post by original_jamingrit on 2008-03-31
I'm not sure how to solve this problem, but a temporary fix could be to turn off desktop effects.  System->Preferences->Appearance.

This is a problem of mine as well, but since I have older Intel graphics I never used compositing anyways.  It's a gtk problem where you need to force the dpi at startup with the command:
```
startx -- -dpi 96
``` instead of using gdm, which is the normal graphical login.

Hopefully, somebody could come up with a more elegant fix, but if worse comes to worse you'll just have to either delay desktop effects every time you boot, or replace gdm with a text login and startx.  I could never figure out how to force the dpi with gdm.

---

### Post by sirisaac87 on 2008-03-31
OK so is there a way to make it so that every time i log in that this window title bar will be normal size?

---

### Post by sirisaac87 on 2008-03-31
I dont know how to make my title bar normal, I change it to 10 font and then it looks like the screenshot above, then I try and fix it by turning it to 1 and its so small I cant see anything..Is there a way to fix this problem for good?? Please help me

---

