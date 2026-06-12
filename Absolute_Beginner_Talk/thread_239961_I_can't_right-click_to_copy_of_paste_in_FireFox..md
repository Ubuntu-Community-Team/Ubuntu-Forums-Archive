---
title: "I can't right-click to copy of paste in FireFox."
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-08-20
When I right click in a text box I get a back/forward/reload/stop/etc. box when I should be getting a cut/copy/paste/delete/etc box appearing. Why is this?:-k (I tried taking a picture, but the print screen button apparently doesn't work with a right click menu open)

Also, while I have your attention I have another question (I remember it being answered in another thread, but I can't find that thread for the life of me) 

When I click on the address bar the cursor appears where I clicked instead of highlighting the whole URL. This makes it hard to type in addresses. Well, not hard, but it costs me two or three extra keystrokes, and I sure do hate being wasteful.

---

### Post by aysiu on 2006-08-20
I don't know about your first question, but for your second question, try one of these:

F6
Alt-D
Control-L

or... if you must use the mouse...

about:config in the address bar and look for browser.urlbar.clickSelectsAll and toggle it.

---

### Post by Amablue on 2006-08-20
Thanks, the about:config was what I was looking for. Hot keys are my prefered method (thanks by the way, I knew about Alt+D, but not the other two) but there are times where the mouse is just more convienient.

---

### Post by aysiu on 2006-08-20
I'm really not sure about your first problem. I'm getting paste in my context menu for text boxes.

Is this something that's just been happening recently?

---

### Post by Amablue on 2006-08-20
No, it's been a problem as long as I've been on ubuntu, I'm just trying to fix up the remaining little things that bother me. 

It works fine in smaller text boxes. I also get the correct menu to pop up when I right click the search bar or the title bar. But if I try it on a large text box, like the one I'm typing the message in, it doesn't show up with that same box. Instead it pops up with the menu that shows up when I right click on any arbitrary point on the page. 

How'd you take that picture by the way? I the save picture dialog box doesn't appear when I have a menu box open.

---

### Post by aysiu on 2006-08-20
Nope. Works for me in larger text boxes, too. Again, not sure what the problem is. Have you tried other browsers (Epiphany, Opera, Konqueror) to see if it's just a Firefox thing? Have you tried a fresh Firefox profile to see if it's extensions or themes that may be messing with your context menu?

The screenshot is using Gnome's built-in screenshot tool. To get it to take a shot while I have the context menu open, I use the command: ```
gnome-screenshot --delay 5
```

---

### Post by Amablue on 2006-08-20
Okay, it works in safe mode, so it must be an extention. Now just a process of elimination to figure out which one is causing it. 

I can take it from here. 

Thanks again, aysiu.

---

