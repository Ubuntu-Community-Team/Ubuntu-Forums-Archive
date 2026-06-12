---
title: "View curses application via ssh?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by pormogo on 2006-09-26
I was wondering if it was possible to view a curses application already running on a remote machine through SSH. I understand that if you start a screen session and then connnect via ssh and connect to the screen session that it should work, but is it possible to do this without having to use screen? I kinda wanted to check on a torrent I have running with btlaunchmanycurses.bittornado. Thanks for the help :)

---

### Post by pormogo on 2006-09-26
bumping this one really quick

---

### Post by andypaxo on 2006-09-26
EDIT:
 Didn't read your post fully.
 skymt is correct - If the program is already running you can't connect to it

- - - - - - - - - -

Yep, curses applications run over SSH fine.
Just tried running one now - and got colors and everything.

(You know that you can even connect to X-Windows with SSH?)

---

### Post by skymt on 2006-09-26
There's no way to do it with a program that's already running. Just use screen in the future.

---

