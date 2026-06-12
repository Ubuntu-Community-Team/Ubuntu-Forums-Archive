---
title: "[SOLVED] convert .chm to .pdf file"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-11-21
Is there any way possible to convert a .chm file to a .pdf file.  A friend sent me several documents in .chm format and I can not read them at all.  If any one has the slightest idea how to convert these files then please write.

PS.- Tried xchm reader for Linux and don't like the look or feel of the program.

---

### Post by John E on 2006-11-21
Does your friend still have the original HTML files that he would have used to make the CHM files? It's not an ideal solution but I think you'd fare a bit better if you could get hold of them.

Alternatively, if your friend can open the CHM files on his machine (which is presumably running Windows) ask if he can convert them to PDF format. A utility like DocuCom should do this easily.

---

### Post by alienexplorers on 2006-11-21
Thanks for the help.  Not sure if he saved them or not.  Just found them on the web somewhere and thought about me when he sent them.  Don't know why he used .chm format, but he did.  I would have preferred .pdf myself.

---

### Post by jrjazzman on 2006-11-21
> **alienexplorers said:**
> 
PS.- Tried xchm reader for Linux and don't like the look or feel of the program.

I felt the same way at first.  I did a little adjusting of fonts by clicking the font button in xCHM and now I like it pretty well.  Sorry I don't know the answer to your question.

---

### Post by adamkane on 2006-11-21
gnochm.

kchmviewer.

Conversions are nasty. You're better off screenshotting each page, saving them as TIFs, and joining them together as a PDF.

---

### Post by Oki on 2006-12-12
There is; [http://madphilosopher.ca/2006/09/how-to-convert-chm-files-under-linux/](http://madphilosopher.ca/2006/09/how-to-convert-chm-files-under-linux/)

After running the program you will have a folder with html files. Use the program htmldoc from Synaptic to convert them into a PDF file.

---

### Post by silver6 on 2007-03-19
That worked great Oki, thanks for that.

---

### Post by devicerandom on 2007-09-24
(Know to come late, but it can be useful for someone) You can also try this tool I put online: [http://code.google.com/p/chm2pdf]("http://code.google.com/p/chm2pdf") ;)

---

### Post by odieman on 2007-12-30
> **devicerandom said:**
> (Know to come late, but it can be useful for someone) You can also try this tool I put online: [http://code.google.com/p/chm2pdf]("http://code.google.com/p/chm2pdf") ;)

And here you have got all the information about chm2pdf from it's author :-)
[http://www.karakas-online.de/forum/viewtopic.php?t=10275](http://www.karakas-online.de/forum/viewtopic.php?t=10275)

---

### Post by SOULRiDER on 2007-12-30
> **odieman said:**
> And here you have got all the information about chm2pdf from it's author :-)
[http://www.karakas-online.de/forum/viewtopic.php?t=10275](http://www.karakas-online.de/forum/viewtopic.php?t=10275)

I was actually looking for something like this too, I'm gonna check it out and see how well it performs :)

Thank you!

---

### Post by odieman on 2007-12-30
For Ubuntu users, there is a guide:
[http://code.google.com/p/chm2pdf/wiki/HowToInstall](http://code.google.com/p/chm2pdf/wiki/HowToInstall)

this is short and precise follow-through for installing all the dependencies before installing the 'chm2pdf' it self (just scroll down to the comment), I just tried it and it works great :-), indexed PDF out of .chm file - sweet :-)

I just did one change - did not install the 'pdftk' - since author of the 'chm2pdf' script made changes to it and 'pdftk' is not needed any more ... works fine for me (tried).

---

### Post by kindofabuzz on 2008-03-25
[http://www.harshj.com/2007/12/06/convert-chm-files-to-pdf-in-linux](http://www.harshj.com/2007/12/06/convert-chm-files-to-pdf-in-linux)

---

### Post by Jose Catre-Vandis on 2008-03-30
This a great little script

Ubuntu Gusty requires the following:

Ubuntu/Kubuntu:

    * libchm1
    * libchm-bin
    * libchm-dev
    * python-chm
    * html-doc
    * htmldoc-common

---

### Post by shr2004 on 2008-05-30
I have installed chm2pdf by using synaptic package manager. I am trying to convert a C++ book. However there is something wrong going on here. After I give the command it start to convert, after doing some conversion it then stack at a line given here:

match temp0626_html	match replace it with temp0626.html

It does this operation 626 times and then stop here without making any progress in the terminal. When I press ctrl+c, I got this information:

Traceback (most recent call last):
  File "/usr/bin/chm2pdf", line 887, in <module>
    main(sys.argv)
  File "/usr/bin/chm2pdf", line 883, in main
    convert_to_pdf(cfile, filename, outputfilename, options)
  File "/usr/bin/chm2pdf", line 305, in convert_to_pdf
    page = re.sub(match_string, replace_string, page)
  File "/usr/lib/python2.5/re.py", line 150, in sub
    return _compile(pattern, 0).sub(repl, string, count)
  File "/usr/lib/python2.5/re.py", line 239, in _compile
    p = sre_compile.compile(pattern, flags)
  File "/usr/lib/python2.5/sre_compile.py", line 507, in compile
    p = sre_parse.parse(p, flags)
  File "/usr/lib/python2.5/sre_parse.py", line 679, in parse
    p = _parse_sub(source, pattern, 0)
  File "/usr/lib/python2.5/sre_parse.py", line 314, in _parse_sub
    itemsappend(_parse(source, state))
  File "/usr/lib/python2.5/sre_parse.py", line 419, in _parse
    subpatternappend((LITERAL, ord(this)))
KeyboardInterrupt

Any suggestion/help from anyone?

Thanks

---

