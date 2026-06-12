---
title: "pdflatex and evince problem"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by elexhobby on 2007-04-22
Hi..

I'm a newbie and learning latex.. When I convert tex files into pdfs using pdflatex, the pdf file created contains an orange clock on its icon and doesn't open using evince.. It just says "Loading..." However, the same pdf file opens cleanly using xpdf.. Could somebody please explain me the reason of this weird behavior?

---

### Post by engla on 2007-04-22
Sounds really strange, evince doesn't fail a lot. Would you mind attaching the source .tex file and/or the pdf?

---

### Post by elexhobby on 2007-04-22
Surprisingly, it is working now.. But that's just lucky.. You can never predict when it'll work and when not.. and the icon remains weird.. Normally, the first page of the pdf should be the icon. Anyways, I'm attaching the files here.

---

### Post by elexhobby on 2007-04-22
Working fine now when I restarted my computer.. I wish I understood what goes on behind all this.. Currently at least, it seems all "beyond logic" to me..

---

### Post by engla on 2007-04-22
I'm sorry I can't tell you why or how that went. Hopefully it works forever after now.. I never had any problems like this. Good luck! :)

---

### Post by frisket on 2007-04-23
Probably because you're using \usepackage{times} which is deprecated. Try changing times to mathptmx and see what happens. See [http://www.ctan.org/tex-archive/help/Catalogue/entries/mathptmx.html](http://www.ctan.org/tex-archive/help/Catalogue/entries/mathptmx.html) for details.

---

