---
title: "ThinkpadR40 numlock not working"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-10-09
Hello,

I have a ThinkPad R40 and use the built-in keyboard. Now, although everything works fine it would be nice for the games to have the keypad activated. For that I need to use the NumLock. Now, the button worked fine with the preloaded windows, but it has no effect on X. Is there a way to reactivate the key?

Cheers,
Sidd

---

### Post by jfinkels on 2007-10-09
> **siddartha said:**
> Hello,

I have a ThinkPad R40 and use the built-in keyboard. Now, although everything works fine it would be nice for the games to have the keypad activated. For that I need to use the NumLock. Now, the button worked fine with the preloaded windows, but it has no effect on X. Is there a way to reactivate the key?

Cheers,
Sidd

I'm not really sure how to fix your problem exactly, but I can show you two tools that may help you.

'xev' is a program which shows you keypresses, mouse events, etc. Type the following in the terminal to start it:```
xev
```

'xmodmap' is a program that allows you to display or remap keys on your keyboard, etc. To display all mapped keys and the associated events, type the following:```
xmodmap -pke
```

Use Google to search around for how to use xmodmap to help you reassign an action to the numlock key, and read more about these two commands with:```
man xev
``` and ```
man xmodmap
```

---

