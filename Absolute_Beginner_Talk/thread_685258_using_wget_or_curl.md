---
title: "using wget or curl"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jimw on 2008-02-02
I'm having problems trying to download just a certain section of a site (example:  [http://www.gilmanstudio.com/display.php?id=29](http://www.gilmanstudio.com/display.php?id=29))

Best I've been able to do is using wget with the -r option, but that not only gets me that section but carries on and hauls down the whole site.

Anybody got any good suggestions?

JimW

---

### Post by PaulFr on 2008-02-02
IMHO, you may be better off looking at **[http://www.gilmanstudio.com/print.php?id=29](http://www.gilmanstudio.com/print.php?id=29)**, i.e. the print version of that page.

I think something like ```
wget -k -l 1 -r -p -np http://www.gilmanstudio.com/print.php?id=29
``` will work. This will download all the images and css files required (-p), convert any remaining links (-k) and limit depth to 1 from the start page (-l 1). Hope this helps.

---

### Post by jimw on 2008-02-02
> **PaulFr said:**
> IMHO, you may be better off looking at **[http://www.gilmanstudio.com/print.php?id=29](http://www.gilmanstudio.com/print.php?id=29)**, i.e. the print version of that page.

I think something like ```
wget -k -l 1 -r -p -np http://www.gilmanstudio.com/print.php?id=29
``` will work. This will download all the images and css files required (-p), convert any remaining links (-k) and limit depth to 1 from the start page (-l 1). Hope this helps.


Thanks a lot, and specially for indicating the function of all the options involved.

Next question is, 'How can I put these downloaded files together in a file so that I can move quickly from one to the next using OpenOffice?

That is, put the lot of them in one html page. (I think thats what I'd need, at least.)

Thanks again

JimW

---

### Post by PaulFr on 2008-02-03
I am not sure of the best way to do this, but one way could be:```
sudo apt-get install htmldoc
cd www*/OnLine_Class
htmldoc --webpage -f ~/Desktop/lessons.pdf Lesson??.htm Lesson???.htm "Final Words".htm
```will convert these pages to a large PDF file (not so good formatting).

More instructions for htmldoc are at **[http://www.easysw.com/htmldoc/docfiles/toc.html](http://www.easysw.com/htmldoc/docfiles/toc.html)**

---

### Post by jimw on 2008-02-03
> **PaulFr said:**
> I am not sure of the best way to do this, but one way could be:```
sudo apt-get install htmldoc
cd www*/OnLine_Class
htmldoc --webpage -f ~/Desktop/lessons.pdf Lesson??.htm Lesson???.htm "Final Words".htm
```will convert these pages to a large PDF file (not so good formatting).

More instructions for htmldoc are at **[http://www.easysw.com/htmldoc/docfiles/toc.html](http://www.easysw.com/htmldoc/docfiles/toc.html)**

Thanks again, Paul.

I've done a pdf of it, and I'll do some fooling around with htmldoc to see what else it's capable of.


Jim

---

