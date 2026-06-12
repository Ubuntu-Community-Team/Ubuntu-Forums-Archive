---
title: "How can I edit a .prn file?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2008-04-06
I want to be able to edit a .prn file. Specifically, I want to change the preview image. I'm not sure how to do this, as GIMP won't open this and google is not cooperating. Any advice? 

All help is much appreciated.

---

### Post by Dynaflow on 2008-04-07
LaTeX maybe?

You might be able to turn it into a PDF with Ghostscript and then use PDF Editor to edit it also.

---

### Post by Dynaflow on 2008-04-07
Okay, I have a better answer.

Convert to PDF:
```
ps2pdf yourfile.prn yourfile.pdf
```

Install PDFEdit
```
sudo apt-get install pdfedit
```

Edit the thing.  

I'm not sure about how to get it back to PRN again, but where there's a will, there's a way.

---

### Post by rouge568 on 2008-04-07
Well, pdfedit keeps crashing when I try to edit the file, and it has no way to turn it back to a .prn anyways. How do you make one of these files in the first place?

---

### Post by Dynaflow on 2008-04-08
PRNs are DOS printer-output files.  They're what result when you "print to file," at least in Microsoftland.  

What are you trying to do with this PRN file?

A couple of things:  You may want to grab the latest version of PDFEdit from Debian Unstable: [http://packages.debian.org/sid/pdfedit]("http://packages.debian.org/sid/pdfedit").  The version in the Hardy repos is rather old.

Also, were you successful in converting the PRN to a PDF for editing in the first place?

---

### Post by rouge568 on 2008-04-08
Ok, upgraded pdfedi and was sucessful in converting it to PDF, though I don't really think this is the way to go. The .prn file has a preview image, and I want to change it. At the same time, it's a printer config text file and I want to keep that intact. (I don't think a pdf has the ability to retain all this information)
However, I found a way to do what I needed in the first place, so this whole process is now extraneous.

---

### Post by Dynaflow on 2008-04-08
Would you mind posting the solution you found here for posterity, in case anyone else has a similar question in the future?

I'm also pretty curious now, myself.

---

### Post by rouge568 on 2008-04-09
Oh no - I didn't ever get the prn file edited. See, I'm trying to find the right drivers for my printer (not easy), and I finally found a free one that worked. The only problem is that it splotched a big fat logo over ever page I printed. That logo was displayed on this .prn file, and I was going to change it to transparency (deleting it just made a grey box where the logo was). But now I found some drivers that work, so my problem is solved.
Editing this file should be something that I am able to do, however, and it would be nice to have the knowledge and tools to do so.
And thank you for all your help.

---

