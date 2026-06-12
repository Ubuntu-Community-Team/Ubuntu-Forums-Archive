---
title: "[SOLVED] Permission to make new folder"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by rchokler on 2008-02-05
I have read an article how to install some fonts,
there for i need to make my own folder under /usr/share/fonts/truetype
but i don't have the option to do that (gray bottom)
Do i need to change some permissions ?

---

### Post by stchman on 2008-02-05
> **rchokler said:**
> I have read an article how to install some fonts,
there for i need to make my own folder under /usr/share/fonts/truetype
but i don't have the option to do that (gray bottom)
Do i need to change some permissions ?

I have a tutorial on font installation in Ubuntu.

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

---

### Post by fenian on 2008-02-05
The easiest way to install new fonts is to do this...
Open a window and hit ctrl+l to show the location bar.In the location bar type...

fonts:///

you can drag and drop the fonts you want to add into that window.

---

### Post by rchokler on 2008-02-05
Sorry doesn't work
command not found  -- on  sudo apt -get isntall msttcorefonts

and on your suggestion some error

---

### Post by p_quarles on 2008-02-05
> **rchokler said:**
> Sorry doesn't work
command not found  -- on  sudo apt -get isntall msttcorefonts

and on your suggestion some error
Check the spelling on the first one:
```
sudo apt-get install msttcorefonts
```
On the second one, use your file manager rather than Firefox.

---

### Post by jan quark on 2008-02-05
well to make a new folder try this

```

sudo mkdir /path/to/folder/you/want
```

---

