---
title: "where do newly installed programs go?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by johnmxg12 on 2006-12-02
hey guys i just installed a new program using the terminal, 

```
sudo apt-get install imagemagick
```

and i'm having a hard time finding this program.  i checked in my graphics/multimedia/other sections and i couldn't find it.  so where do all the newly installed programs go if they dont show up in these directories from the pull down menus?

---

### Post by Jussi Kukkonen on 2006-12-02
imagemagick is a collection of command line commands, isn't it? That's why it doesn't show up.

Files are installed all over the plase: configuration in /etc, executables in /usr/bin, and so on. *man imagemagick* will no doubt tell you the commands you need to use. That said, you can check where the files are installed from e.g. synaptic.

---

### Post by bapoumba on 2006-12-02
imagemagick is a command line tool. Please read **man imagemagick** for details ;)

---

### Post by lumpki on 2006-12-02
If you want to use Imagemagick interactively, try this. Open a terminal and type **display**. You can Grab a screenshot or browse to an image and Open it. Now left-click on the image to bring up a floating menu. There you go!

---

