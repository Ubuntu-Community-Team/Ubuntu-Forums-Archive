---
title: "reassign a single key"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by chefjames on 2007-09-07
My problem is that the backspace and up arrow keys have stopped working on my laptop keyboard.   I am looking for a way to change what a single key does when I press it.  I do not need to change the whole keyboard or to assign complex functions or make any special characters.  All I want to do is make some other key that I don't use be the key that I need.  For example: can I make the F12 key be the Backspace key.

I have tried looking on the formus but have not found what I need.  Most of the time I was referred to ~System>Preferences>Keyboard>Layout Options~.  If you can reassign a single key using this I can't  figure it out. 

One post mentioned finding the keycode using something called "xev" and "xmodmap" in a terminal.   xev showed me what was happening not what the keycode was.  xmodmap was not helpful either.  I could not figure out how to use xmodmap even if I had the keycode.

Maybe there is a neat little program or application that I can download.

If anyone knows for a fact that this cannot be done please let me know.  

Many thanks in advance.

---

### Post by Hoag on 2007-09-07
I think

```
xmodmap -e "keycode 96 = 0xff08"
```

should make the F12 key work as the backspace key. I had the same problem with my h key when some fool *cough, shifty eyes* spilt a drink in the keyboard and had to make the windows key act as h. You'd need to type the command every time I log in though, which is a hassle (unless someone smarter than me knows how to do it a better way).

---

