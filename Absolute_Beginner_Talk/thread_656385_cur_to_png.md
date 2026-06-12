---
title: "cur to png?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-01-02
or .cur to anything for that matter...

---

### Post by ~LoKe on 2008-01-02
Do you have...a question?  Are you trying to convert cur to png?

.cur files are images for cursors.  Wouldn't you want to convert png to cur, and not the other way around?

---

### Post by Niklas Schröder on 2008-01-02
yeah.  i want to convert .cur to .png.  i know they're cursors.  but i don't think you can use .cur in ubuntu.  let me know if i'm wrong...  but i'm trying to adapt a windoze cursor set to ubuntu...

---

### Post by ajgreeny on 2008-01-02
I think you could be right as I can't get any .cur files to open with anything,  The answer may be to convert them in windows if you have it, or get someone with windows to do it for you first and then use them however you want.

---

### Post by Niklas Schröder on 2008-01-02
*that* would be the easy way.  ;)  i don't want to have to use multiple operating systems.  there has to be something out there that can solve the problem.

---

### Post by Slotos on 2008-05-30
Just making reply so this topic has at least one solution.

sudo apt-get install imagemagick
convert file.cur file.png

---

### Post by noynac on 2008-05-30
> **Slotos said:**
> Just making reply so this topic has at least one solution.

sudo apt-get install imagemagick
convert file.cur file.png

I agree that Imagemagick is the way to go. The following table provides useful information as to the file formats handled by Imagemagick. As you can see, Imagemagick can read CUR files, which can then be written to PNG or many other formats:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

---

