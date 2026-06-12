---
title: "Using LaTeX in Linux / Ubuntu"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by natman on 2005-09-17
Hi i am about the partition my compaq laptop to be dual boot ( Win XP and Ubuntu), i have never used linux before.

at the moment i use a program called winedt to write in LaTeX in windows, I need to know how to obtain LaTeX for Linux ubuntu and also how to get a program for LaTeX called Xfig.

I heard that these come with some linux disrib's is this true , if so does it come with ubuntu and what is it like compared to winedt?
thank you

---

### Post by macgyver2 on 2005-09-17
[QUOTE=natman]Hi i am about the partition my compaq laptop to be dual boot ( Win XP and Ubuntu), i have never used linux before.

at the moment i use a program called winedt to write in LaTeX in windows, I need to know how to obtain LaTeX for Linux ubuntu and also how to get a program for LaTeX called Xfig.

I heard that these come with some linux disrib's is this true , if so does it come with ubuntu and what is it like compared to winedt?
thank you[/QUOTE]
Hi natman...have you been following the [other thread]("http://www.ubuntuforums.org/showthread.php?t=66124") you started?  There have been a lot of replies there since you posted.

---

### Post by natman on 2005-09-17
Yeah , i had a good luck at it, but it has just turned into a disscussion on what latex does for you,

and the first reponce was kinda hard to follow, i just want a simply answer that a windows person can understand.

I really did not mean to clog up foroums really sry.

---

### Post by Leif on 2005-09-17
in a terminal type "sudo apt-get install tetex-extra kile". 

if you prefer a GUI approach, you can achieve this by starting system->administration->synaptic, search for tetex, mark tetex-base, tetex-bin and tetex-extra, search for kile, mark that too, then install them all.

then use kile to edit instead of winedt.

---

### Post by macgyver2 on 2005-09-17
[QUOTE=natman]Yeah , i had a good luck at it, but it has just turned into a disscussion on what latex does for you,

and the first reponce was kinda hard to follow, i just want a simply answer that a windows person can understand.

I really did not mean to clog up foroums really sry.[/QUOTE]
No no, I didn't mean to imply you're clogging up the forums!  I just wasn't sure if you had read that other thread.

So if I'm reading this correctly, you already know LaTeX and you just want to know how to process your LaTeXed document on Ubuntu...

To install it, open a terminal and type
```
sudo apt-get install tetex-base tetex-bin
```
Then if you want the extra tex packages type
```
sudo apt-get install tetex-extra
```
And for xfig, make sure you have universe repositories selected and type
```
sudo apt-get install xfig
```

Now, to process a document that you have LaTeXed you can open a terminal, change to the directory with the document (I'll use paper.tex as an example) and type
```
latex paper.tex
```
I always use the above command twice...sometimes it apparently has to be run more than once to catch all the citations and figure references. Even if you don't need to run it more than once, doing so won't hurt anything, so I always just run it twice.

To get a postscript use the command
```
dvips <options> paper.dvi
```
I threw in the <options> because there are some useful ones that are probably worth knowing...you can take a look at them with [font=Courier New]man dvips[/font].

To get a pdf you can change the postscript into a pdf with the command [font=Courier New]ps2pdf[/font]...or go directly from the .dvi file with the command [font=Courier New]dvipdf[/font].

Edit: I should have thrown this disclaimer in from the start...the above is the way I do it.  There are other ways, too...I'm just not familiar with those ways. :)

---

### Post by natman on 2005-09-17
Look thanks for all the really useful help,just hope it smotthly when i get ubuntu, i might be back again ( hope not )


Can i ask, i have seen some talk about AMD 64 processors around, I have an AMD athlon 64 is this going to cause me any problems?
I only intend to use ubuntu for gap and latex, and simple things.

Thanks again

---

### Post by Leif on 2005-09-17
I don't have a 64-bit processor, so I may be wrong, but from the posts I've seen, the issues with installing the 64-bit version of ubuntu is that some media codecs are not available yet, so playing flash,dvds and such requires some work. The majority of things work just fine, including latex etc. Also, if you need to, you can always just install the 32-bit version of ubuntu.

---

