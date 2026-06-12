---
title: "Vim/Vi editor problem"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Gorky on 2008-02-25
I want to write special Swedish characters when using vim/vi editor.
Those characters are ' Ä , Å and Ö .
This work fine with other distros.
I can work with vim/vi editor. I mean I can make a file

However, I can't write the special Swedish characters with Ubuntu.
How do I fix the problem?
Please help me.

---

### Post by adw on 2008-02-25
what keyboard layout do you have?
(go to: System-->Preferences-->Keyboard to check it).
I've got Generic 105-key(Intl) PC set, and selected language to Norwegian.
So i'm guessing swedish?:-p
At the bottom of that pane, you'll see an "add" button, just click and find your locale:KS

---

### Post by wormser on 2008-02-25
I had similar problems with vi before.  The solution for me ended up installing the full version of vi.  I do not know if it will solve your issue but it is worth a shot.

```
sudo apt-get install vim-full
```

---

