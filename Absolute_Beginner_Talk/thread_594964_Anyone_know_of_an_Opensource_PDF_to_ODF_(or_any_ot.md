---
title: "Anyone know of an Opensource PDF to ODF (or any other format) convertor?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-10-28
Anyone know of a good pdf to odf convertor??  I believe Ive found a pdf to ps convertor, but ps to another format is tricky.  Any suggestions?

---

### Post by Paulmd on 2007-10-28
> **kevdog said:**
> Anyone know of a good pdf to odf convertor??  I believe Ive found a pdf to ps convertor, but ps to another format is tricky.  Any suggestions?

Pdf conversions are generally one way. That said, i've found a project-in-development. You will have to complie it yourself. (this is really annoying). I've not used it myself, so cannot tell you if it works well.

[http://sourceforge.net/project/showfiles.php?group_id=163339](http://sourceforge.net/project/showfiles.php?group_id=163339)

Also, look here.

[http://www.pdfzone.com/category2/0,1874,1851561,00.asp](http://www.pdfzone.com/category2/0,1874,1851561,00.asp)

---

### Post by kevdog on 2007-10-28
Thanks for those links

Ive seen the first link -- however it just converts each page to a jpg or image file so you can write on top of the page like a canvas.  I really need something that I can edit inline

I didnt understand the second link.

---

### Post by Paulmd on 2007-10-28
> **kevdog said:**
> Thanks for those links

Ive seen the first link -- however it just converts each page to a jpg or image file so you can write on top of the page like a canvas.  I really need something that I can edit inline

I didnt understand the second link.

The second link is just information re PDF.

The straight poop:

Making a pdf is a relitavely easy thing: PDF (like postscript) is essensially a printer based format, and many pdf generaters are essensially printer drivers. 

Going the other way isn't so easy.  All the software I've seen is either paid software, windows only, or both. If you have a windows machine available, there are a few options for converting pdf to word, or rtf, which Openoffice can read. It all involves spending money, however. I've seen jack that works on linux. (see below for stuff that is supposed to work for windows)

PDFs have been traditionally made by creating the document in another format, and using Adobe's utility to print them out. Adobe's acrobat writer itself is very limiited, you can do simple text edits, insert and delete pages, and rotate them. Not a whole lot else. 

The free tools for creating editable documents from pdf presently either (a) just make images, or (b) extract the text and trash the formatting. Little more than you can do with copy and paste. The tool google uses for searching pdfs does more or less the same. When you click "view as html" in google, you get a html page with almost no formatting (google would do better if it were easier).

The tools that do more than this are generally not trivial projects, and the developers want money for their efforts.


Yes openoffice reads Word just fine: but all this stuff is windows based, none is opensource. maybe at least one of them will work in wine or similar:

 
[http://www.pdfpdf.com/pdfconverter.html](http://www.pdfpdf.com/pdfconverter.html)

Windows only, acrobat 6 or earlier formats, not open sourse, or free. There is however a demo)

[http://www.verypdf.com/pdf2word/index.html](http://www.verypdf.com/pdf2word/index.html)
Windows only, 30 day trial, converts to word

[http://www.pdftransformer.com/pdf-to-rtf/](http://www.pdftransformer.com/pdf-to-rtf/)
Several similart toos for word, excel, html and rtf. there is a trial version.


The one product htat MIGHT meet allyour criteria is KWord. I saw one post on a forum that suggests that KWord has the ability to open a pdf and save it in Openoffice format. With the caveat "do not expect miracles" Koffice's site doesnt methiton this.

[http://www.oooforum.org/forum/viewtopic.phtml?t=27360&highlight=](http://www.oooforum.org/forum/viewtopic.phtml?t=27360&highlight=)
[http://www.koffice.org/](http://www.koffice.org/)

Edit: just tried koffice: seems to work OK.
In the command line:

sudo apt-get install koffice

---

### Post by kevdog on 2007-10-28
Ill definitely try koffice.  I tried some of the pay products as trials on windows.  They worked but not perfectly -- not sure if they would be worth the $50. 

Thanks for the plethora of info.  Just makes me want to hate Adobe more.

---

