---
title: "Script (?) question"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by xmastree on 2005-08-16
Not sure if this is the correct forum, but here goes...

I've been using XNveiw to automagically generate web pages containing photographs.

What it creates is a directory of your choosing, containing one or more html pages, and two subdirectories. One for the actual images and one for the thumbnails.
All very nice and easy, but...

I now want to change the background colour of the index pages to match the rest of the site. There are 31 of them, mostly they're called Page.html, but some are Page2.html, Page3.html depending on the number of images in that set.

Is there some command I can run, or a script which will search and replace text without doing them one by one?

---

### Post by Juergen on 2005-08-16
This is what 'sed' is for.
But 'info sed' will probably make you want to leave your colors as they are ;-)
Read it anyway if you find yourself with too much free time.

But for quick success, here is a small HOWTO showing 2 other ways to do it:
[http://www.debian-administration.org/articles/197](http://www.debian-administration.org/articles/197)

---

### Post by xmastree on 2005-08-17
[QUOTE=Juergen]This is what 'sed' is for.[/QUOTE]```
rpl above_quote "sed"  "rpl" *
```  ;-)

Cheers

---

### Post by Juergen on 2005-08-17
Just wait until you need regular expressions... :-)

---

