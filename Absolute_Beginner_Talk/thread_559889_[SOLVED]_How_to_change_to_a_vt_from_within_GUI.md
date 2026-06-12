---
title: "[SOLVED] How to change to a vt from within GUI ?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-25
I know this probably sounds utterly ridiculous, but I like to experiment with new things.
Before everyone gets out in left field, I **do** in fact comprehend that I can use my keyboard and press CTRL + ALT + F2 - F6 to access my virtual terminals.

Now, here is my question.
Is there any way possible to *change* to one of those virtual terminals without the pressing of the key combination on my keyboard, but rather, typing in a command in gnome-terminal ?

I know... utterly ridiculous, but still, I would like to see if it is possible.

Dr Small

---

### Post by Dr Small on 2007-09-26
I found out that while in a virtual terminal, the command:
```
chvt 1
``` 
will take me to Virtual Terminal 1, and if I press ALT + Right (or left), it changes between the virtual terminals, but the above command does not work while in X.

Dr Small

---

### Post by Dr Small on 2007-09-27
I found out from capink, [here](http://ubuntuforums.org/showpost.php?p=3438026&postcount=5), that I can use "sudo chvt *number*" to change displays, even while in a GUI, which is what I wanted to be able to do.

So, I added chvt to my sudoers list, with NOPASSWD, and then created an alias for sudo chvt to chvt, so now I don't have to use sudo. It works rather nicely. I know, I'm lazy :p

[SOLVED]


Dr Small

---

