---
title: "[SOLVED] Please help - title bars gone!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-11-14
I got into compiz, and I think I shouldn't have. Now things are really screwed up, and I don't know how to restore what I had.

Problem: I have no title bars. Sorta.

If I open a terminal and type "gtk-window-decorator" then my title bars appear, and everything seems to be fine. As soon as I close the terminal, I lose the title bars and everything goes to hell.

In addition, as soon as I type in "gtk-window-decorator" and hit enter, I don't get another prompt in the terminal. In order to get another prompt, I have to close the terminal window (which makes my title bars go away) and reopen another one.

I just want my title bars back the way they were, without having to have the terminal running (and disabled!!) the whole time I'm on.

---

### Post by sc30317 on 2007-11-14
sudo apt-get install emerald
ALT+F2
emerald --replace

---

### Post by doctorbighands on 2007-11-14
I installed emerald. Now my title bars are red instead of orange.

Hitting ALT-F2 doesn't seem to do anything.

When I closed the terminal, I lost the title bars again.

---

### Post by doctorbighands on 2007-11-14
Wait a minute - it worked now. Thank you!

Can I make my title bars orange again instead of red? I liked that much better.

---

### Post by PeterJS on 2007-11-14
You were on the right track, when you run a command in a termainal by default it runs in the forground which means it has sole control over that terminal untill  it finishes. Which in the case of gtk-window-decorator it finishes when your desktop session is over. However by putting an & after a command will run it in the background, which will give you a propmt back right away. When you get the prompt back you can safely close it by typing exit, don't just close the window that will take the terminals background processes with it, while exit will not.

Long story short try: "gtk-window-decorator &" and then "exit"

---

### Post by PeterJS on 2007-11-14
To slow on the post, you can change the look of your windows by running the emerald-theme-manager.

---

### Post by doctorbighands on 2007-11-14
Thanks everybody. I have it just how I like it now!

---

### Post by overdrank on 2007-11-14
> **doctorbighands said:**
> Thanks everybody. I have it just how I like it now!

great please marked as solved under thread tools! :KS

---

