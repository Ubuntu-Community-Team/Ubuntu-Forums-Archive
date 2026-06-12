---
title: "Can you make html to pdf?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-08-08
I was thinking if it was possible to make this guide [http://linuxcommand.org/](http://linuxcommand.org/) to pdf, so I dont have to Open it in a browser, and also the ability to scrool down in pdf viewer instead of pressing next in the browser.

---

### Post by dmizer on 2006-08-08
well all of the open office utilities have the ability to create pdf documents.  it might be a bit tricky to pull off, but i'm sure it could be done using one of the many tools available to you in the office suite.

---

### Post by hashimoto on 2006-08-08
The clumsy and simple way:

First print the page to a post-script file (*.ps) from the browser.
Then convert the printed .ps file to pdf by using ps2pdf in terminal. Simple as that.

A more refined way is to install the pdf-printer in cups. See this thread: [http://www.ubuntuforums.org/showthread.php?t=188860&highlight=print+pdf](http://www.ubuntuforums.org/showthread.php?t=188860&highlight=print+pdf)

---

### Post by Jucato on 2006-08-08
There's a utility in the repositories called *htmldoc*. You might want to give it a try.

---

### Post by jincast90 on 2006-08-09
> **Fenyx said:**
> There's a utility in the repositories called *htmldoc*. You might want to give it a try.

It costs money.
It isint that important to me.

---

### Post by Jucato on 2006-08-09
it doesn't cost money. It's in the repositories. It's in the main repositories, and nothing in the main repositories cost money.

---

### Post by robins_web on 2006-08-09
Open the HTML file in AbiWord, KWord or OpenOffice. Then save it as PDF.

---

### Post by jincast90 on 2006-08-09
> **robins_web said:**
> Open the HTML file in AbiWord, KWord or OpenOffice. Then save it as PDF.

Can I downloade the html file? Or how should I open it in office?

---

### Post by blackest_knight on 2006-09-20
hopefully this is useful htmlhelp.exe  will decompress a .chm file into regular html (windows tool)(microsoft helpfile format often used for ebooks).
htmldoc will take in the html and create a pdf.
there is a commercial version and a gpl version. the gpl version is in the repositories.
synaptic package manager can find and install it for you.
htmldoc is brilliant just order your documents as required.

---

### Post by szf on 2006-09-20
Just to put it out there... The YesLogic people, behind [Prince]("http://www.princexml.com/"), have worked out exactly that thing. It starts at ~ $350 USD, however.

That said, I've read a [paper]("http://www.windley.com/archives/2006/07/a_reputation_framework.shtml") that can be d/l in pdf format, thx to Prince. It does a handsome job.

---

