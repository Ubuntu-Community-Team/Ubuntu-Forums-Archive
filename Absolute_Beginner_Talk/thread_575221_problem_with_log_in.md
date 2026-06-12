---
title: "problem with log in"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by raised2b on 2007-10-13
Hi all,

Here's the thing, i'm running feisty and everything was fine. Then i ran ntfs-config and that all went good and well. After rebooting however, when i logged in and gnome started a terminal automatically opens and a window to my ntfs drive, not a big deal but the big problem is that all my windows don't have the borders and are positioned at the top of the screen. also, my window workspace selector on my top panel is MIA although all my other panel objects are there and working fine, the other thing i noticed was that the keyboard won't work at all.

HELP!

Thanks!

ps- when i boot in fail safe gnome everything seems to be fine

---

### Post by ajmorris on 2007-10-13
hi, in order to fix this, i need to know which Window Manager you are using, in terms of gnome, kde etc.

---

### Post by raised2b on 2007-10-13
i'm running gnome

---

### Post by raised2b on 2007-10-14
please help

---

### Post by raised2b on 2007-10-14
bump

---

### Post by sayuki288 on 2007-10-14
sudo aptitude install ubuntu-desktop

---

### Post by raised2b on 2007-10-14
ok..... what does that do and how is that going to help, it looks to me like that would do a complete reinstall...

---

### Post by raised2b on 2007-10-15
so nobody can help me here huh?!

---

### Post by bodhi.zazen on 2007-10-15
Sounds unusual, are you sure you did not run another window manger like Beryl or Compiz ??

At any rate, at the terminal type :

```
metacity --replace
```

---

### Post by raised2b on 2007-10-18
hi bondhi, thanks for the reply

the command didn't work, and i'm certain i'm not running another window manager.  but i know that's the problem b/c when i boot in failsafe gnome the splash screen before the desktop shows up has three little icons, when i boot into my normal login there are only two so for some reason i'm missing something when my session loads.  here's a copy of my xsessions-errors log.  i've been all over google and forums trying to fix this

 thanks for any help

---

### Post by raised2b on 2007-10-26
still looking for some help on this one... anyone?

---

