---
title: "Panels are gone...can't put them back on."
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-20
I accidentally xkilled my bottom panel and it made both my top, and bottom panel disappear.

I had a program (Grip) that got frozen (scratched CD) and I tried to alt/F2-->--xkill it, and right after I had pressed run for xkill, the force quit option happened for the Grip. So I selected force quit, but my cursor was still a "X" for the xkill option. I didn't have any other programs on the desktop to xkill, but I did have my thunar file system running minimized on the task bar.

So not thinking and not knowing how to stop the xkill process, I clicked on the task bar on my bottom pannel to hopefully xkill my home folder, and I "xkilled" my bottom panel by accident. It also made my top panel disappear.

I didn't worry because I thought that I could just add a new panel from my Applications-->--Settings-->--Settings Manager-->--Panel, but when I click on it, nothing will happen like it used to when you could set the pixel width, auto hide, and add new panel. Every thing else works perfectly.

I have Beryl AiGLX as my window manager running on xubuntu edgy xfce4.

Thanks for any help.

---

### Post by loell on 2006-12-20
press alt + f2 , then run xfwm4

---

### Post by crimesaucer on 2006-12-20
Thanks, is that going to work with bery running?

***Edit.- that didn't work.

---

### Post by crimesaucer on 2006-12-20
Still not working, I'm thinking it's because of Beryl being my window manager. What do you think? 

Can I fix this in .config or .gconfig?

---

### Post by loell on 2006-12-20
you can "killall beryl-manager" then do previous intsruction, then start beryl manager again.

---

### Post by crimesaucer on 2006-12-20
You know what, you were almost correct with the terminal code "xfce-panel", it just had to have "&" added to the end:

xfce-panel &

Thanks for the help, I have my panels up and running without having to kill Beryl.

---

### Post by loell on 2006-12-20
lol, yep you're right. its xfce4-panel, what was i thinking :-k 
that i typed xfwm4  :mrgreen:

---

### Post by crimesaucer on 2006-12-21
Well...xfwm4 is the window manager so it's an honest mistake. I should of looked through the forum search a bit more before posting anyway because I found a thread with a similar problem pretty quickly with the solution "xfce-panel &" and that worked very good.

Thanks for the help anyway.

---

