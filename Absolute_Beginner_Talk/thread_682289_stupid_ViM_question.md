---
title: "stupid ViM question"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Alberio on 2008-01-29
So I just started using ViM, and I'm trying to wean myself off of the arrow-keys. I'm using command mode and hjkl to move around and x to delete, (except for when I use backspace in insert mode)
but when you use hjkl to move to the end of a line of typing, it's highlighting the last character. So, when you go to insert mode, it's actually one character away from the end. I don't know how I would move over that one character without using the arrow keys.
Would somebody tell me how?

Thank you,
      Alberio

---

### Post by p_quarles on 2008-01-29
Use "a" to enter insert mode after the current character. The link in my signature has a couple of good Vim tutorials, too, if you're interested.

---

### Post by taurus on 2008-01-29
Make sure you have installed the vim-full package.

```
sudo apt-get update
sudo apt-get install vim-full
```

---

### Post by Alberio on 2008-01-29
> **p_quarles said:**
> Use "a" to enter insert mode after the current character. The link in my signature has a couple of good Vim tutorials, too, if you're interested.

Thank you , that did it :popcorn:

---

### Post by ekravche on 2008-01-29
get gvim (graphical vi improved), it's a better editor...

---

### Post by asmoore82 on 2008-01-29
in the full version of ViM,
capital 'i' will go to the beginning of the line and enter Insert mode
and capital 'a' will do the same at the end of the line.

---

### Post by bcrom on 2008-01-29
Here is a handy reference sheet:

[http://www.cs.rit.edu/~cslab/vi.html](http://www.cs.rit.edu/~cslab/vi.html)

---

### Post by macogw on 2008-01-30
> **p_quarles said:**
> Use "a" to enter insert mode after the current character. The link in my signature has a couple of good Vim tutorials, too, if you're interested.

"a" means "append," for reference.  Another trick is to use "A" which appends at the end of the line, so you don't even have to hit $ to jump to the end then "a" to append.  Instead, it's all one keystroke.  Inserting at the beginning of a line is, likewise, "I" (capital i).

---

