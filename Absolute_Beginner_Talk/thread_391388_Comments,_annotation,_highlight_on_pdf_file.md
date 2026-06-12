---
title: "Comments, annotation, highlight on pdf file"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by eagletek on 2007-03-23
Hello everybody!

usually when I read pdf - since most of the times I don't print them - i make annotations directly on it or highlight some parts of the text. In windows it is possible using the adobe acrobat pro or using the reader whenever the original author has authorized the permission of annotations and commenting.

I was looking for something similar under linux, and I was not able to find anything... 
:-(

What I need, is either a reader able to comment, highlight the text (saving it in the same  pdf file) or a tool that given a pdf is able to enable the annotation permissions so that i can do it with the reader.  I tried pdftk but without any results.

do you have any idea?

thanks,
eagletek

---

### Post by zvacet on 2007-03-23
Evince

---

### Post by eagletek on 2007-03-24
I tried evince, but I can't comment, mark the text!
are you sure?

byez
eagletek

---

### Post by eljalill on 2007-03-24
As far as my research goes, only acrobat writer and foxit reader can do that.
Writer is too expensive for my taste, and there is no Linux version, at least there wasn't when I last looked.
Foxit reader does exist for Linux, but it didn't want to run on my little baby, so I am using the Foxit reader for windows with wine, which works, once you applied a patch. Look here:
[http://www.ubuntuforums.org/showthread.php?t=378272](http://www.ubuntuforums.org/showthread.php?t=378272) 

If you need more help with this, let me know.
Foxit runs nicely with this for me, only the search funktion is somewhat impaired..

---

### Post by j4play on 2007-07-06
> **eagletek said:**
> Hello everybody!

usually when I read pdf - since most of the times I don't print them - i make annotations directly on it or highlight some parts of the text. In windows it is possible using the adobe acrobat pro or using the reader whenever the original author has authorized the permission of annotations and commenting.

I was looking for something similar under linux, and I was not able to find anything... 
:-(

What I need, is either a reader able to comment, highlight the text (saving it in the same  pdf file) or a tool that given a pdf is able to enable the annotation permissions so that i can do it with the reader.  I tried pdftk but without any results.

do you have any idea?

thanks,
eagletek

yeah i'm trying to look for the same thing.  the best i've managed is using an adobe professional 30 day trial version to enable commenting, then using acroread (in windows or linux) to comment/highlight/etc..

would be nice if there was some command line tool to enable commenting, bu i've been unable to locate such a tool...

---

### Post by dwblas on 2007-07-06
Since I only do this a couple of times a year, I convert to postscript, both pdftops or pdf2ps are already installed.  There are many postscript engines that can then be used.  I also found this link that says that flpsed will do what you want.  I haven't tried it.
[http://www.linux.com/articles/113907](http://www.linux.com/articles/113907)

---

### Post by Balachmar on 2007-07-26
I want to do the same thing, now somebody told me that okular should be able to do the trick, but I can't seem to be able to install it on Feisty. I keep getting errors...
I really think something like this should be added to evince...

---

### Post by zorkerz on 2008-03-17
This thread is getting old but i was wondering what solutions if any you guys settled on? Mostly I just want to highlight text though comments would be nice to. This functionality in Evince would be preferred for me as well.

---

### Post by TexMex657 on 2008-03-23
Same, I would also like to know if you guys found any solutions to your problem.

Cheers!

---

### Post by zorkerz on 2008-03-24
no i gave up as it was not worth eenough to me. pdfedit is linux native and in the repos, which makes it the easiest. It does not fit with gnome gui well. The free windows versions i tried in wine were not much good. Nothing felt right to quite meet my needs, although there were deffinately do the stuf I wanted them to just not in to eligant of a matter.

---

### Post by lucathecat on 2008-03-25
There's a web-based way of doing this if you are interested in that route? It is at [http://a.nnotate.com](http://a.nnotate.com)   You get quite a few free pages and then its a few cents/page. The neat thing is that all your notes get indexed too.

---

### Post by zorkerz on 2008-03-25
thats pretty cool im not sure its a viable business model for long though

---

### Post by chandra on 2008-05-29
Have you seen this thread:

[http://ubuntuforums.org/showthread.php?t=387750](http://ubuntuforums.org/showthread.php?t=387750)

---

### Post by saperduper on 2008-06-26
check this out
*"Xournal is an application for notetaking, sketching, keeping a journal using a stylus. It is free software (GNU GPL) and runs on Linux (recent distributions) and other GTK+/Gnome platforms"*
[Xournal]("http://xournal.sourceforge.net")

---

### Post by gsoundsgood on 2008-07-12
xournal does a great job, and satisfies my needs...perfect highlighting, and quick notes with the mouse....

i do have problems typing notes...but i don't really care, it does a great job....
i had to install xpdf viewer to get it to import pdf correctly...all in the repositories...

---

