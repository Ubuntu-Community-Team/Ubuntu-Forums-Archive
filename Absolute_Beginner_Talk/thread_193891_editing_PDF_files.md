---
title: "editing PDF files"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by davors on 2006-06-10
Is there any tool I can use to edit PDF files? In particular, I need to crop PDF files. Basically looking for a free tool with small subset of features that Acrobat has. Thanks.

---

### Post by Hanj on 2006-06-10
There's a package in the repositories called pdftk which seems to do what you want.

---

### Post by davors on 2006-06-10
[QUOTE=Hanj]There's a package in the repositories called pdftk which seems to do what you want.[/QUOTE]

thanks - does everything I need but cropping - so if anyone knows another tool that does cropping too it would be great!

---

### Post by Hanj on 2006-06-11
Well, I don't know that much about this, I just did a search for "pdf" in Synaptic and saw what popped up. There seem to be several apps there, so you might want to do a search for yourself. Also, I hear Scribus is good for pdf editing.

---

### Post by JanVH on 2006-06-11
[This link]("http://applications.linux.com/article.pl?sid=05/01/06/0612209") is explaining how to edit PDF's, but it notices too there's no great linux PDF editor arount.

---

### Post by hugmenot on 2006-06-11
There&#8217;s a CLI tool in TeTeX called pdfcrop:```
PDFCROP 1.5, 2004/06/24 - Copyright (c)
2002, 2004 by Heiko Oberdiek.
Syntax:   pdfcrop [options] <input[.pdf]> [output file]
Function: Margins are calculated and removed for each page in the file.
Options:                                                    (defaults:)
  --help              print usage
  --(no)verbose       verbose printing                      (false)
  --(no)debug         debug informations                    (false)
  --gscmd <name>      call of ghostscript                   (gs)
  --pdftexcmd <name>  call of pdfTeX                        (pdftex)
  --margins "<left> <top> <right> <bottom>"                 (0 0 0 0)
                      add extra margins, unit is bp. If only one number is
                      given, then it is used for all margins, in the case
                      of two numbers they are also used for right and bottom.
  --(no)clip          clipping support, if margins are set  (false)
  --(no)hires         using `%%HiResBoundingBox'            (false)
                      instead of `%%BoundingBox'
  --papersize <foo>   parameter for gs's -sPAPERSIZE=<foo>,
                      use only with older gs versions <7.32 ()
Examples:
  pdfcrop --margins 10 input.pdf output.pdf
  pdfcrop --margins '5 10 5 20' --clip input.pdf output.pdf

```

---

### Post by aysiu on 2006-06-11
Use KWord.

It can import PDFs, edit them, and then export them again.

The export option isn't obvious, though. You have to go to Print, and instead of printing to a printer, you "print" to PDF.

---

### Post by hugmenot on 2006-06-11
This import is likely to cause troubles with the PDF because it will try to extract and convert the text etc. This is not what Acrobat does when it deals with PDF files.

---

### Post by LxP on 2007-01-28
You can also use one of the tools in the pdfjam package to crop pages.  I don't remember which one at the moment, but it's a function available within another utility offered by pdfjam (maybe pdfjoin or pdfnup).

---

### Post by rsambuca on 2007-01-28
You know, usually one thread should be enough for these questions.:-x

---

