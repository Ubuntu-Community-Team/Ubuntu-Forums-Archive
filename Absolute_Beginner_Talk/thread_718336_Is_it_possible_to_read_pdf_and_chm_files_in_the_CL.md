---
title: "Is it possible to read pdf and chm files in the CLI?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-03-08
I have a Ubuntu server that I absolutely love.  I've got some pdfs and chm files I store on it that have really great information I'd love to be able to read directly in the CLI.  Is this possible?

---

### Post by ghostdog74 on 2008-03-08
some tools you can use, xpdf, acroread ( acrobat reader for linux) for PDFs
one tool i know of, kchmviewer ( using KDE ) for chm files. 
search google for more of such tools...

---

### Post by HermanAB on 2008-03-08
Something like this I guess:
$ ps2ascii file.pdf | less

---

### Post by handy on 2008-03-08
> **F4RR4R said:**
> I have a Ubuntu server that I absolutely love.  I've got some pdfs and chm files I store on it that have really great information I'd love to be able to read directly in the CLI.  Is this possible?

I suspect that you don't have a GUI desktop installed & that is why you need to use the CLI?

Under those circumstances I can't help you.

---

### Post by oxsyn on 2008-03-08
> **handy said:**
> I suspect that you don't have a GUI desktop installed & that is why you need to use the CLI?

Under those circumstances I can't help you.

No GUI, don't want it.  Trying to become a CLI junkie.

---

### Post by PeterJS on 2008-03-08
> **HermanAB said:**
> Something like this I guess:
$ ps2ascii file.pdf | less

Hey that's pretty cool. I never even knew that existed, just tried it out, it worked pretty well it didn't render perfectly, it got a bit upset about page breaks and page numbers, and having the text in 80 character columns that wasn't intended to wrap at that width looked kinda funny but that can't be helped.

---

### Post by rev on 2008-03-21
> **F4RR4R said:**
> No GUI, don't want it.  Trying to become a CLI junkie.

As for CHM, you can use extract_chmLib utility from libchm-dev and read output HTMLs with your favorite text-based WWW browser.

---

