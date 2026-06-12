---
title: "[SOLVED] Converting PDF to document file"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-02-27
Hi, I'm not sure if I'm being a little dim but I can't seem to convert a PDF to OpenOffice file.  I've downloaded Adobe 8 for Linux (after trying other open source apps.) but try as I might I'm failing!  I simply want to convert a pdf application form for a research project into a document file so I can edit it.  It has text boxes included in the pdf but when I convert it - at present using Adobe and the other apps - it just has the text.  Any ideas gratefully recieved.

---

### Post by jeffus_il on 2008-02-27
Kword in Kubuntu does it:
[http://ubuntu.wordpress.com/2007/04/10/convertimport-from-pdf-and-keep-the-formatting/](http://ubuntu.wordpress.com/2007/04/10/convertimport-from-pdf-and-keep-the-formatting/)

---

### Post by pedro_orange on 2008-02-27
Or you can use the shell utility:

```
pdftotext
```

[http://en.wikipedia.org/wiki/Pdftotext](http://en.wikipedia.org/wiki/Pdftotext)

Should be already installed in Gutsy.

---

### Post by SOULRiDER on 2008-02-27
> **pedro_orange said:**
> Or you can use the shell utility:

```
pdftotext
```

[http://en.wikipedia.org/wiki/Pdftotext](http://en.wikipedia.org/wiki/Pdftotext)

Should be already installed in Gutsy.

Doesnt that convert to plain text? That could be a problem, the document would most likely lose formatting and any imeages.

---

### Post by vishzilla on 2008-02-27
use online converters like [http://media-convert.com/](http://media-convert.com/)  & [http://zamzar.com/](http://zamzar.com/)

---

### Post by pedro_orange on 2008-02-27
> **SOULRiDER said:**
> Doesnt that convert to plain text? That could be a problem, the document would most likely lose formatting and any imeages.

-layout 
Maintain (as best as possible) the original physical layout of the text. The default is to 'undo' physical layout (columns, hyphenation, etc.) and output the text in reading order.

---

### Post by Berean on 2008-02-27
That's great guys, thank you.  However, I seem to lose the formatting when I convert from pdf to OpenOffice 2.3.  The boxes are there but so much smaller than in the original.  It has to be EXACTLY as the original pdf.  Any further ideas? (Media Convert did it, but lost the formatting).

---

### Post by pedro_orange on 2008-02-27
Lol Screenshot?

I know you can use PDFtoPS and keep formatting.
Does it have to be .odf

---

### Post by Berean on 2008-02-27
No, it doesn't have to be odf, but I do need to edit it and keep the original format to submit to a university.  How do I do a screenshot?

---

### Post by pedro_orange on 2008-02-27
Convert it to Postscript then, thats editable. That also has a command line utility:

```
pdftops
```

Why don't you just edit the PDF?

You can screenshot using the "Prt Scr" or "Printscreen" key found on your trusty keyboard ^^
It will save it as a .PNG image

---

### Post by Berean on 2008-02-27
That would be ideal, but I don't seem to be able to do that!  Unless I'm being daft with that as well.

---

### Post by pedro_orange on 2008-02-27
I'm sorry I don't follow? 

You are unable to take a screenshot of your screen?

Can you do: 

```
gnome-screenshot
```

If you can you just need to check your keyboard shortcuts.

If you can't do pdftops check the man page or go here: [http://linux.die.net/man/1/pdftops](http://linux.die.net/man/1/pdftops)

Or if you can't edit the PDF, thats probably cause its locked for editing. I'm sure there are tools out there if you google it.

---

### Post by Berean on 2008-02-27
Sorry pedro_orange, I have misled you.  I can do a screen-shot.  What I can't do is edit the pdf.  However, due to a screaming son - wanting food - I logged off and then restarted and used synaptic manager and now have PDF Editor which I CAN now edit the file.  Thanks so much for your help, advice and perseverance: it's very much appreciated.

---

