---
title: "Feisty: Metacity Keybinding command problem"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Kurt_Alan on 2007-07-15
I am trying to set a keybinding command for xkill.  The advice I'm following from aysiu fails:

1. First, he says to double click in the space next to a command, but the error message I get is: "Currently pairs and schemas can't be edited."  However, if I right click I can try New Key and enter xkill.  However, what do I do about Type? Leave it at the default Integer?  And how about Value?  Leave it at the default 0?

2. O.K. I add xkill as a keybinding (but I don't know if I did it correctly, but when I go to Global Keybinding to add my shortcut, it is not listed. . . 

I don't remember all these problems in Dapper Drake. . .

---

### Post by Kurt_Alan on 2007-07-15
I have solved part of the problem.  I needed to check Configuration Editor.
But I'm still failing to get xkill to function.
Here's what I've done:
1. From keybinding_commands I selected command_1 and right-clicked "Edit"
2. For Value I entered xkill.

So now I have:
command_1         xkill
So far so good (I hope).

3. Now I go to global_keybindings.  command_1 is not on the list, so I add it as a new key.
4. It appears as command_1 with a Value of 0. So I change Integer to String and now I put in my Value as <Ctrl>A
5. FAIL!  The keyboard shortcut for xkill doesn't work.

What am I doing wrong?

---

### Post by rugburns499 on 2007-09-24
im new but...
under global keybindings, you don't want "command_1" instead you want "run_command_1"

---

