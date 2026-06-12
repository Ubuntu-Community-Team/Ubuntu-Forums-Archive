---
title: "making posters in Latex"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-10-08
This might not be the correct forum for this question, but I am still posting it with the hope that someone who uses Latex regularly will come across it and others will graciously ignore it.

I am trying to make a a0 size poster for a conference with Latex. To do so I will need the following packages: a0poster, textpos and everyshi. So I downloaded the following packages from CTAN:

a0poster
textpos
everyshi

Now I need to save them at an "appropriate place" (i.e., at a place where
Tex scans for input files). I looked at the Tex FAQ and read that files
with .sty, .cls or .fd extensions need to be saved in:

$TEXMF/tex/latex/<package>

where $TEXMF is the local root of the texmf tree. (The relevant portion of the FAQ is here [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=wherefiles](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=wherefiles))
 
To find the local root on my machine I did:

```
kpsewhich -expand-var "\$TEXMFLOCAL"

```
and got

```
/usr/local/share/texmf

```
But when I try to copy the files a0poster.cl or a0size.sty into

```
/usr/local/share/texmf/tex/latex/

```
I see that the directory does  not exist! Infact, when I try to see if
the following directory exists:

```
cd /usr/local/share/texmf
```

I get a message: "no such file or directory".

Can anybody see the mistake I am making? Basically I need to place the files in a place where TEX scans for input files. Any adivice will be greatly appreciated.

Thanks.

---

### Post by jordanmthomas on 2006-10-08
Not sure if it will help, but there does exist a 
/usr/share/texmf/*...stuff you're talking about*

Maybe try putting it there?

---

### Post by aam-aadmi on 2006-10-08
I tried that early on, but it does not work.

---

### Post by jordanmthomas on 2006-10-08
Wouldn't you also need to reset your $TEXMF variable to point to the actual place?

```
export TEXMF=/usr/share/texmf/
```

---

### Post by podunk on 2006-10-08
Did you ry creating a directory where the program expects it to be?

```
cd /usr/local/share
```

```
sudo mkdir texmf
```

make sure it's there with no typos
```
ls -la | less
```

Press "q" to exit less.

Then copy your files.

A disclaimer – I don't know a thing about your program – but! I just got finished winging it on Samba. I had to give up doing it the right way with my set up and did what the computer wanted to do and it worked out grand. :-D

---

### Post by aam-aadmi on 2006-10-09
You are absolutely right. Once I created the directories and copied the files there, everything worked fine. Thanks.

---

