---
title: "How can I get my PrtSc key to work?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by braka on 2008-01-14
I'm using xubuntu for my old laptop (about eight years old) and like most other laptops, it has a PrtSc key (print screen) but it doesn't work?

Is it possible to make it work in any way?

Or maybe it just doesn't cooperate with gimp?

And at last, I'm a complete beginner to this, so please be patient and as non-technical as possible :)

---

### Post by braka on 2008-01-14
Doesn't anybody know how to do this?

---

### Post by thelatinist on 2008-01-14
Be patient.  Far fewer people here use xcfe than use Gnome (which supports PrtScrn out-of-the-box).  It may take time for an answer; please don't bump the thread.

---

### Post by braka on 2008-01-14
I'm sorry.
I didn't mean to be annoying, I just needed it to work, like  - now, because I have to use it  in school tomorrow. I have never needed it before, so when I found out it didn't work, I was really annoyed. I cannot do what I have to use it for tomorrow, if it doesn't work.
But then we'll just think about another solution, I guess.

The reason I wrote what I wrote in the last post , is, that I was afraid I might be in the wrong forum (English is not my mother tongue, so sometimes things doesn't come out right :))

---

### Post by p_quarles on 2008-01-14
The super-quick, sure-fire fix is like so. In a terminal, run:
```
sudo apt-get install gnome-screenshot
```
If it says "already at newest version," no worries. Next, run the app:
```
gnome-screenshot &
```
There's also a GUI way to do this, but you said you're in a hurry, and that's the quickest, foolproof way I can think of.

---

### Post by santiagoward2000 on 2008-01-14
Personally, I've set **scrot** to do this, I didn't want to install **gnome-screenshot**.
But well, once you installed one, you need to set a keyboard shortcut for it. Go to **Applications/Keyboard Settings** and under the **Shortcuts** tab, add a new theme. Then click on the other **Add** and add the command for that one, ```
gnome-screenshot
``` for example.
Cheers!

---

### Post by jordanmthomas on 2008-01-14
Also, if you are using gimp it has a built-in screen capturer.
file -- acquire -- screenshot

---

### Post by braka on 2008-01-15
Thank you so much all of you :D

I'll see if I can get it to work :D

---

### Post by thelatinist on 2008-01-15
If you do, be sure to post back here and mark the thread [Solved].

---

