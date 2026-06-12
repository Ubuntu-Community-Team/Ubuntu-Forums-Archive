---
title: "Command history in terminal"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by handler on 2007-09-25
The keyboard shortcuts to access the command history (up/down arrows, Tab to complete the command and such...) don't seem to be working. For example, when I press the up arrow, I get: ```
$ ^[[A 
```

I get the same thing when I press the other arrow keys (except the "A" changes for a "B", "C" or a "D"). If i press the Tab key, i just get a tab space... Does anyone know how to solve this issue?
Please dumb down your explanations to the maximum as I am a newb.

Thanks!

---

### Post by bodhi.zazen on 2007-09-25
Just a guess, but sounds like you have a mis match with your keyboard and some of the keys.

1. does this happen in a terminal (in X) and/or in a consul (Ctrl-Alt-F1) ?
2. Are other keys affected ? Do the arrow keys work in less or within a command ?
3. What shell are you using ?
4. Did you modify .bashrc (assuming bash shell) ?

And, what keyboard are you using ?

---

### Post by handler on 2007-09-25
1. It does this in terminal. As for the consul (I tried it for the first time tonight, how do you get out of there?), the problem seems to be the same.

2. Are other keys affected? Well, like I said earlier, pressing Tab will give me a tab space instead of completing the command I started. Other than that, the mapping seems ok. Even the accents work like they're supposed to (é, ç, ê, etc.). The arrow keys work as expected in other programs.

3. What shell? I think it's bash. I'm using the Terminal application that seems to be standard in version 6.10 of Ubuntu.

4. No, I don't remember making changes to .bashrc.

I'm using a microsoft natural "internet" keyboard.

Thanks for the help!!

---

### Post by Dr Small on 2007-09-25
> 1. It does this in terminal. As for the consul (I tried it for the first time tonight, how do you get out of there?), the problem seems to be the same.


CTRL + ALT + F2 will take you to a virtual terminal.
CTRL + ALT + F7 will take you back to your x display.

Dr Small

---

