---
title: "Remap control key in gnome-terminal?"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by nzlemming on 2010-05-02
I just installed Ubuntu to get more familiar with it since I'll be using it in a new job shortly. I use Macs at home and in my current job, so I'd like to make it as Mac-like as possible. I've remapped the command and control characters using the following .xmodmap:
  
[FONT=Courier New]remove control = Control_L Control_R
remove mod4 = Super_L Super_R
add control = Super_L Super_R
add mod4 = Control_L Control_R
[/FONT]  
Which works great for everything except the terminal, since Ctrl-C is now mapped to CMD-C, and still conflicts with what I'd like to use to copy. Is there any way I can remap the Control key just for the terminal? I'm willing to consider gnome-terminal alternatives if required.

---

### Post by llamabr on 2010-05-02
In gnome terminal, you can change the keyboard shortcuts:

edit>keyboard shortcuts.

---

### Post by nzlemming on 2010-05-03
Unfortunately this doesn't help. The problem is that I can't reconfigure how to make the terminal send control characters. Since I have control mapped to the command key, ctrl-c is now command-c, which conflicts with copy. On the Mac this works well since control is separate from command, I'd like to replicate this on Linux by making mod4 (instead of control) send control characters.

---

