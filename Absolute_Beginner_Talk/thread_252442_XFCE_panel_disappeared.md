---
title: "XFCE panel disappeared"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by thornmastr on 2006-09-06
I am running Kubuntu and want to use XFCE. It gives me an interesting problem. If I am running only one session and using XFCE I get no panel (the top horizontal bar) with the Applications drop down, and whatever programs  chosen to reside on the panel bar. I have no idea as to where it has gone or, more importantly, how to get it back. 

What is most interesting, at least to a novice like me, is that if I use the standard Gnome session, and then log into a second session using XFCE, it comes up perfectly with the panel present and acting just like it should always act.  So, my question is, how do i get my panel to appear when I am using XFCE in my first session, ie, when I log on using the XFCE shell?

Thanks for both suggestions and commentary.](*,)

---

### Post by bodhi.zazen on 2006-09-06
IMO XFCE has had some stability problems of the panel nature. It could be either the panel or applets (additions to panel).

To track down, start XFCE. Open a terminal.

Type:
```
xfce4-panel
```.

google search the error message. In my experience the exact error message changes and there may or may not be a solution.

Often the solutions are temporary.

Too bad because I otherwise have enjoyed XFCE but stopped because of these issues a few moons ago. Sorry to see they still persist.

---

### Post by enopepsoo on 2006-09-06
If you still have your bottom panel, maybe right click it and go 'add new panel.'

there is also that nifty xfce feature where you can right click the desktop to get your application menu (I can't tell you how many times I have started Mahjong this way).:mrgreen:

---

### Post by thornmastr on 2006-09-07
Thank you both for the replies. Bodhi, I think you are correct. I googled and searched numerous web pages and found nothing of great value to helkp correct the problem. Even the message from xfce4-panel was not too helpful but certainly very obvious.  "Panel missing.".
Enopepsoo, I have no bottom panel either, and right clicking the desktop does not give me the application menu. I think for now I will wait for a more stable vrsion of XFCE.

---

### Post by bobosity on 2006-09-17
I was messing around and killed my panel AND right mouse button menus. Figured out how to run xfce4-panel in a terminal.

So what script do I edit to make the panel come back at startup?

How do I bring back my right mouse menus?

thx

---

### Post by picpak on 2006-09-17
Don't know if this will help, but maybe try deleting the ~/.config/xfce4 folder?

---

### Post by bobosity on 2006-09-17
Thanks!  That worked.  :p

---

