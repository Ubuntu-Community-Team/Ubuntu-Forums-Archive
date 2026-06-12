---
title: "Printing pdf file"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-09-16
I have received a .pdf file by email and I would like to print it out.
I can open the file with KGhostView but when I go to print it on my Brother CP110C printer (which does work properly) I get a message "Printing failure: Could not convert to PostScript"
If I try to "print to file (PostScript)" I get the same error message.
Do I need to install some other converter? How and where do I get it?

---

### Post by tonymoloney on 2007-09-17
Bump

---

### Post by perce on 2007-09-17
Try to convert it to a postscript file using pdf2ps: in a terminal just type pdf2ps file.pdf. If it works, you'll find a file called file.ps in he same directory. You can click on it to open it in a viewer, or print it with the command lpr file.ps. Of course you must put the name of your file
where I write file.

---

### Post by tonymoloney on 2007-09-17
Thanks Perce. I did that and here's the output I got:


tony@tony-laptop:~$ pdf2ps /home/tony/Newsletter.pdf
Error: /undefined in obj
Operand stack:
   5   0
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1889   1   3   %oparray_pop   1888   1   3   %oparray_pop   1872   1   3   %oparray_pop   1755   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1143/1684(ro)(G)--   --dict:0/20(G)--   --dict:70/200(L)--
Current allocation mode is local
Current file position is 23
GPL Ghostscript SVN PRE-RELEASE 8.60: Unrecoverable error, exit code 1
tony@tony-laptop:~$


Any help?

---

### Post by perce on 2007-09-17
> **tonymoloney said:**
> 
Any help?

Not really :( Something like that happened to me long time ago, and I don't remember how I solved it, if I solved it at all. One thing you should try is to install the latest Acrobat Reader from Adobe and see if it works. By the way, does this mess happens only with that file or with every pdf?

---

### Post by tonymoloney on 2007-09-17
That's the only .pdf file I've got.
Do I actually have to install pdf2ps or is it already on my system, as I have assumed?

---

### Post by perce on 2007-09-17
> **tonymoloney said:**
> That's the only .pdf file I've got.
Do I actually have to install pdf2ps or is it already on my system, as I have assumed?

You already have pdf2ps: if you try to start a program you don't have from the command line the error you get is "command not found", so clearly pdf2ps started, tried to do something, and failed. 

You can find a lot of pdf files to test here: [http://www.arxiv.org/list/math/new](http://www.arxiv.org/list/math/new).

---

### Post by tonymoloney on 2007-09-17
OK. I grabbed one of those files and got exactly the same error.
This looks like it's going nowhere, so, as I can still read my newsletter on-screen, I think I'll wait until the next update of Kubuntu is released next month.
I'm using 7.10 Alpha2 which I guess is not 100% bug-free.

---

### Post by perce on 2007-09-17
Sorry for not being more useful :(

---

