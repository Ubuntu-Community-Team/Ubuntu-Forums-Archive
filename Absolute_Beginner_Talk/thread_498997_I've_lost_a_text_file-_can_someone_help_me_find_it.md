---
title: "I've lost a text file- can someone help me find it?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-07-12
Grateful for help on what is surely a simple question for people who understand command line stuff better than I do.

I need urgently to find all the files, written in open office, and probably saved as either .odt or .doc, which contain the text wolfstone <EDIT> in the body of the file </EDIT> 

The files are on one of three computers, and to simplify things I'd like to run the same search separately on all three

This is typical CLI stuff I'm sure but I've got my back to a deadline and I just don't have time to search out and experiment with a new skill- thanks in advance

---

### Post by Inxsible on 2007-07-12
> **ginestre said:**
> Grateful for help on what is surely a simple question for people who understand command line stuff better than I do.

I need urgently to find all the files, written in open office, and probably saved as either .odt or .doc, [COLOR="Red"]which contain the text wolfstone[/COLOR]

The files are on one of three computers, and to simplify things I'd like to run the same search separately on all three

This is typical CLI stuff I'm sure but I've got my back to a deadline and I just don't have time to search out and experiment with a new skill- thanks in advance
I am assuming that the file name consists of the word wolfstone in it as opposed to the word wolfstone being a word in the text body of the file
Try this

```
find -iname / *wolfstone*.odt
``` if that doesnt result in anything use the .doc extension like ```
find -iname / *wolfstone*.doc
```

What the command does: finds the file under / (root) with any characters before wolfstone and any characters after wolfstone with the extension as odt or doc

---

### Post by Inxsible on 2007-07-12
A GUI way to do it would be :
Places --> Search for Files.

If the file name contains wolfstone put that in, else expand the 'Select more options' and enter 'wolfstone' without quotes in 'Contains the text'. There are a bunch of other available options that you can filter by

---

### Post by ginestre on 2007-07-12
Thanks for the quick reply, but unfortunately I wasn't clear- I've amended the original post to clear up the misunderstandiing.  The text wolfstone is IN the file, not in the filename.  So I need to search through a large collection of text files, either odt or doc, to pull out a list of all those that contain the text Wolfstone. If I could also make that search output a a list ordered by date, I'd be the happiest bunny on the planet this morning.

---

### Post by Inxsible on 2007-07-12
> **ginestre said:**
> Thanks for the quick reply, but unfortunately I wasn't clear.  The text wolfstone is IN the file, not in the filename.  So I need to search through a large collection of text files, either odt or doc, to pull out a list of all those that contain the text Wolfstone. If I could also make that search output a a list ordered by date, I'd be the happiest bunny on the planet this morning.

If you try the GUI method i listed before, it does have a Modified Date filter that you can apply on the search

---

