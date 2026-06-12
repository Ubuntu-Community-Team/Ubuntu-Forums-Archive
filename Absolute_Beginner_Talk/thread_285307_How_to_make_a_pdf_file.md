---
title: "How to make a pdf file?"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by nikolaos on 2006-10-26
This is propably a (very) easy one. How do i convert a simple text file into pdf format?

---

### Post by Metacarpal on 2006-10-26
OpenOffice Writer has an Export to PDF function in the File menu.

---

### Post by aysiu on 2006-10-26
I think even Gedit has an Export to PDF option.

---

### Post by Qrk on 2006-10-26
> **aysiu said:**
> I think even Gedit has an Export to PDF option.

Yup, its under the print dialog.

---

### Post by davmac on 2006-11-11
I've just been stunned to find a fantastic little trick. Just about everything seems to be able to print to PDF!

When you print, if you check the "print to file" option, and when requested for the file name give it something like mytestprint.pdf - hey presto it creates a pdf.

I'm still running through testing out different apps, but everything I've tried so far is working (Firefox, Thunderbird, GIMP).

Dave Mac

---

### Post by ron999 on 2006-11-11
Hi davmac
I've just tried what you suggested with Firefox.
It certainly does allow me to create a testprint.pdf file - but Acrobat Reader won't read it afterwards!
Back to the drawing board:-k :cool:

---

### Post by rrwo on 2006-11-11
There's also a CUPS printer driver to create a pdf file.```

sudo apt-get install cups-pdf
```

---

### Post by davmac on 2006-11-11
> **ron999 said:**
> 
It certainly does allow me to create a testprint.pdf file - but Acrobat Reader won't read it afterwards!
Back to the drawing board

You're right! I use evince as my PDF reader and it works fine, but it won't open in Acrobat Reader :(

Dave Mac

---

### Post by rrwo on 2006-11-14
> **ron999 said:**
> Hi davmac
I've just tried what you suggested with Firefox.
It certainly does allow me to create a testprint.pdf file - but Acrobat Reader won't read it afterwards!
Back to the drawing board:-k :cool:

Note this:```

$ file testprint.pdf
testprint.pdf: PostScript document text conforming at level 3.0

```

Maybe because it's a postscript file, not a PDF.  Evince and other programs will recognise the file type anyway and do the right thing. Acrobat only understands PDFs.

Naming the file a PDF does not make it a PDF file.

---

### Post by wastrel on 2006-11-14
You can use the ps2pdf program to convert postscript to pdf.

---

### Post by ron999 on 2006-11-14
> **wastrel said:**
> You can use the ps2pdf program to convert postscript to pdf.

Yes wastrel, the website [www.ps2pdf.com]("www.ps2pdf.com")
converts it online to a downloadable pdf file.

---

