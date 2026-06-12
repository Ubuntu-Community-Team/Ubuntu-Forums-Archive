---
title: "[SOLVED] how do i install a gtk+ theme?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-09-19
In System-> preferences-> themes there is an interface to install themes I've downloaded. I think this should work with GTK+ themes, no?

Anyway I don't know what file to click on to install. Every one I try says "This is not a valid theme" or something similar. I even went into /usr/share and tried to install the Human theme this way and I got the same thing. I tried this with index.theme in each case and sometimes other files if they were present.

What should I do?

Thanks!

---

### Post by yabbadabbadont on 2007-09-19
Make sure that you are viewing the theme details.  Then the controls tab.  Now drag and drop the theme archive file that you downloaded (probably from gnome-look.org) onto that tab.  It should install and then be available for selection.

---

### Post by jordanmthomas on 2007-09-19
If you get a file format invalid error, put the folder that has a .gtk-2.0 directory in it into your ~/.themes folder.

Example:  
```
    
Dyne 
    |___gtk-2.0
             |________other stuff   

```
I'd put the Dyne folder in ~/.themes

---

### Post by dinostabOMG on 2007-09-19
Thanks for the help, guys! For reference, what does it mean when you say ~/.themes ?

I assume the ~ is my username? If so, I don't see a .themes folder in there...

---

### Post by yabbadabbadont on 2007-09-19
~ is a shell variable that expands to your home directory.  In my case it is /home/daffy.  .themes starts with a period, which in unix/linux, makes the file or directory so named hidden normally.  You'll need to enable the option to view hidden files/directories before it will show up.  It is also possible that it doesn't yet exist, if you haven't installed a custom theme before.

---

### Post by jordanmthomas on 2007-09-19
To enable seeing hidden files, just press CTRL + h in nautilus.  You can press it again when you don't want to see hidden files any more.

And, like yabbadabbadont said you might have to make the folder.  It's fine to do this, just make it and put the stuff in there and the gnome theme manager should pick it up.

---

### Post by dinostabOMG on 2007-09-19
Thanks so much!

---

