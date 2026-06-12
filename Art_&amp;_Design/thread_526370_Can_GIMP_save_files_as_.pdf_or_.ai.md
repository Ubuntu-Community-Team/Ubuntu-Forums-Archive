---
title: "Can GIMP save files as .pdf or .ai?"
date: 2007-08-15
forum: Art &amp; Design
---

### Post by kizor on 2007-08-15
My friend wanted me to design something for him, but since I didn't have photoshop I thought GIMP would do.

However he said he needs the file as .pdf or .ai but I can't seem to be able to save as either! :confused:

Am I going to have to download Photoshop and do it through that? :(

---

### Post by smartboyathome on 2007-08-15
Gimp itself does not save to PDF, but you can save it as an image and then import it to OpenOffice.org draw. .ai is a file for illustrator, which is a vector graphics program, and isn't compatible with GIMP (which is a bitmapping program). If I remember correctly, Photoshop does not save as .ai either (for the same reason as stated before). If you would like a program that can save files as .ai, use Inkscape.

---

### Post by kizor on 2007-08-15
Thanks, I try the open office method !

---

### Post by vexorian on 2007-08-15
you could try a PDF printer as well.

---

### Post by bakermiller on 2007-08-16
you ca also use scribus to export .pdf

---

### Post by Half-Left on 2007-08-16
> **smartboyathome said:**
> Gimp itself does not save to PDF, but you can save it as an image and then import it to OpenOffice.org draw. .ai is a file for illustrator, which is a vector graphics program, and isn't compatible with GIMP (which is a bitmapping program). If I remember correctly, Photoshop does not save as .ai either (for the same reason as stated before). If you would like a program that can save files as .ai, use Inkscape.

Both vector graphics and pixmap graphics apps are compatible with each other. The GIMP can import vectors and inkscape can import pixmaps. The idea is that you can composite your SVG done in inkscape with something done in GIMP.

Saving files is like you said so your correct.

---

### Post by graigsmith on 2007-08-17
Inkscape can save adobe illustrator files that are version 8.0

---

### Post by bakermiller on 2007-08-17
> **Half-Left said:**
> Both vector graphics and pixmap graphics apps are compatible with each other. The GIMP can import vectors and inkscape can import pixmaps. The idea is that you can composite your SVG done in inkscape with something done in GIMP.

Saving files is like you said so your correct.

...Yes, but importing vectors in gimp will turn ur vectors into bitmaps:), with no turning back to vectors:) so you are better off compositing your vectors and bitmaps in a compositor app like scribus ( which is the equivalent of indesign) and latter export it as .pdf.


....anyways thats what i do:)

---

### Post by Alexander Grundner on 2009-05-13
> **vexorian said:**
> you could try a PDF printer as well.

I agree with vexorian. The easiest way to get a PDF file from GIMP is to use the print function and then select the PDF option. Works for me :)

---

### Post by transmogrifox on 2009-06-09
> **Alexander Grundner said:**
> I agree with vexorian. The easiest way to get a PDF file from GIMP is to use the print function and then select the PDF option. Works for me :)
 
+1 there.  Check out cups-pdf printer if you don't already have it installed and configured.

---

### Post by kayosiii on 2009-06-10
You won't see any real advantage in exporting files from the gimp as the gimp doesn't store a lot of information as vectors except perhaps the text and paths.

The file format that will let you share the most possible information between Gimp and AI is to save from gimp as a Photoshop PSD file.

If you want a more vector friendly result. I suggest using Inkscape along side the gimp. You can drag and drop layers straight from the gimp into inkscape. and I believe that illustrator can import svg (this will probably get the most information between the two programs, otherwise try some of the other options).

---

### Post by omarkutty on 2009-08-08
I have been trying the print method, but when I press print nothing happens.
I'm clearly missing a step.
 Can anyone help?

---

### Post by alex.rayu on 2009-08-09
No, it cant. GIMP is mostly RASTER editor. AI is expressely VECTOR.
If you want vector, use Inkscape - it's very powerful. If you want PDF, use Open Office - it saves as PDF quite ably. I think I saw Inkscape export to AI, actually, and AI opens Inkscapes's SVG format.

---

### Post by Samhain13 on 2009-08-09
> **omarkutty said:**
> I have been trying the print method, but when I press print nothing happens.
I'm clearly missing a step.
 Can anyone help?

Check out your home folder, if it has a PDF folder in there, look into it.

---

### Post by AlexanderDGreat on 2010-02-05
The challenge with the GIMP's export-to-PDF function is, **you CAN'T select or highlight text.** I created a simple brochure for a company, but when I viewed it, I can't select any text or the company's contact info because they're all pixel. Anyone has a better solution? Thanks.

---

### Post by AlexanderDGreat on 2010-02-07
Hi! Does anyone know how to make a GIMP .xcf file to PDF?

The PDF should be able to highlight and select text as well.

Please help!

PS I'm aware of the export-to-pdf function, but that method wouldn't allow you to select / highlight text inside the file.

---

### Post by punong_bisyonaryo on 2011-02-04
I'd also like to know if you can export each layer as a page in a PDF file. I imported a PDF file into GIMP so I could edit it, unfortunately after all of the work, I didn't know I couldn't save it back as a PDF..bummer!

---

### Post by DMKryl on 2011-02-04
GIMP is a image modification software not a layout program, this exact thing happens all the time in photoshop, photoshop wasn't designed to do that neither GIMP, the correct software is indesing or scribus, for vector work use Inkscape, i don't know why people get so stubborn to try get all the work in one single program, not even Corel who is the program who tries to get all the work (this one was intended to be this way) in a single program is able to do that, if you want a pdf or edit one use scribus maybe inkscape, use gimp to correct or manipulate images, remember the right tool for the right job

---

### Post by prokoudine on 2011-02-05
> **punong_bisyonaryo said:**
> I'd also like to know if you can export each layer as a page in a PDF file. I imported a PDF file into GIMP so I could edit it, unfortunately after all of the work, I didn't know I couldn't save it back as a PDF..bummer!

Only recent development version of GIMP can save PDF and it still won't save pages (yet). Just export layers to images (google for "sg-save-all-layers.scm" — a script that automates that) and use something like gscan2pdf to create PDF from images.

---

### Post by punong_bisyonaryo on 2011-02-06
> **prokoudine said:**
> Only recent development version of GIMP can save PDF and it still won't save pages (yet). Just export layers to images (google for "sg-save-all-layers.scm" — a script that automates that) and use something like gscan2pdf to create PDF from images.

Thanks a lot! This is just what I needed to make things easier (I was about to save each layer one by one when you posted this)

---

### Post by firebird_1979 on 2011-02-06
> **omarkutty said:**
> I have been trying the print method, but when I press print nothing happens.
I'm clearly missing a step.
 Can anyone help?

This method won't actually print anything, it'll put a file on your harddrive somewhere. I believe in your home folder by default, but this can be changed by the user.

If you select "Print to file" in the printer dialogue, you'll also get the option to save to .PDF, .SVG or PostScript.

---

### Post by mikewants on 2011-02-06
Yes, thats right, that Gimp cant save files in .ai.

Use InkScpae :)

---

### Post by prokoudine on 2011-02-06
> **mikewants said:**
> Yes, thats right, that Gimp cant save files in .ai.

Use InkScpae :)

Inkscape doens't save .ai. Neither it saves multipage PDFs until you install one of the few existing extra extensions.

---

### Post by carusoswi on 2011-04-02
> **DMKryl said:**
>  i don't know why people get so stubborn to try get all the work in one single program, not even Corel who is the program who tries to get all the work (this one was intended to be this way) in a single program is able to do that, if you want a pdf or edit one use scribus maybe inkscape, use gimp to correct or manipulate images, remember the right tool for the right job

Stubborn people learn to accomplish tasks in various ways.  I have been searching for about five minutes for an answer to the topic question.  Why would I want to export layers as pages?  Well, I have begun signing documents electronically, some are quite long.  Gimp is handier than many applications in opening multi-page pdf's, and you can control the resolution to keep the pdf image acceptably clear.  Additionally, it is terrific at taking a scan of your signature or initials scrawled out on a piece of paper, and, via scaling and using the curves or level tools, you can enhance an otherwise pale scan to make it quite acceptable when inserted via Gimp into the document at points where you need to initial or sign.

. . . and browsing a document such as this in Gimp is quite convenient, as well.  Just click the layer 'eye' icon to hide one page and expose the next in line.

The problem is, obviously, trying to export the signed document so that you can email it to another party.

I have collected several links, but, rather than post them here, if you do a quick search for Gimp layers to pdf pages, several solutions are readily available.

I came here looking for yet other suggestions.

I've been doing this using Adobe's InDesign (an older version), or you could use Pagemaker (even older) or Scribus.  But, I'm not a script writer, and I've found nothing that will do as good a job on acquiring scans of my hand written signature and cropping them so that they look natural when inserted into a document.

. . . just thought I'd reply to let you know why someone would want to use Gimp in this way.

For me, with InDesign or similar programs, its a matter of importing the pdf image one page at a time into InDesign.

With Gimp, I can import a multi-page pdf, it converts those pages to layers, and, now, I will be able to reverse the process after inserting my signature and any other text that I choose to add.

Seems like a good idea to me.

Caruso

---

### Post by punong_bisyonaryo on 2011-04-03
> **carusoswi said:**
> stubborn people learn to accomplish tasks in various ways.  I have been searching for about five minutes for an answer to the topic question.  Why would i want to export layers as pages?  Well, i have begun signing documents electronically, some are quite long.  Gimp is handier than many applications in opening multi-page pdf's, and you can control the resolution to keep the pdf image acceptably clear.  Additionally, it is terrific at taking a scan of your signature or initials scrawled out on a piece of paper, and, via scaling and using the curves or level tools, you can enhance an otherwise pale scan to make it quite acceptable when inserted via gimp into the document at points where you need to initial or sign.

. . . And browsing a document such as this in gimp is quite convenient, as well.  Just click the layer 'eye' icon to hide one page and expose the next in line.

The problem is, obviously, trying to export the signed document so that you can email it to another party.

I have collected several links, but, rather than post them here, if you do a quick search for gimp layers to pdf pages, several solutions are readily available.

I came here looking for yet other suggestions.

I've been doing this using adobe's indesign (an older version), or you could use pagemaker (even older) or scribus.  But, i'm not a script writer, and i've found nothing that will do as good a job on acquiring scans of my hand written signature and cropping them so that they look natural when inserted into a document.

. . . Just thought i'd reply to let you know why someone would want to use gimp in this way.

For me, with indesign or similar programs, its a matter of importing the pdf image one page at a time into indesign.

With gimp, i can import a multi-page pdf, it converts those pages to layers, and, now, i will be able to reverse the process after inserting my signature and any other text that i choose to add.

Seems like a good idea to me.

Caruso

+1 :ks

---

