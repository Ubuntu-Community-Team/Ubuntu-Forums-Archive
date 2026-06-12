---
title: "CUPS/PDF Change file name"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2008-01-10
I installed the CUPS PDF printer. If I am printing a web page, CUPS will use the page title as the filename. Sometimes the page title remains the same and CUPS/PDF  does not save the document although it appears to have successfully executed the print job (no errors, listed in the "completed jobs"). Is there a way to select the file name under which the print job will be saved as a PDF file (pint to file option will save it as a PostScript file)

Thanks

---

### Post by jonkulp on 2008-01-10
Man, that's like a weird black hole in the .pdf capability of Ubuntu.  I don't understand this either.  I tried doing what you said and the same thing happened.  I couldn't find a file output unless I used the "print to file" checkbox, and then the only option was a .ps file.  I know that Apple's Preview app automatically converts a .ps file to .pdf when you open it, though, because I did this just yesterday.  Not sure how to do the conversion on Ubuntu though.  It seems like you ought to be able to choose the .pdf option no matter where you're printing from.  When I print from a text file, I can make a .pdf directly, but not printing from a web page, as you said.  Weird.  I'll fiddle a bit and see if I can figure it out.

---

### Post by jonkulp on 2008-01-10
Ok, best I can tell, the ability to print to file as postscript is an operating system feature, but the ability to print to .pdf file is a feature of specific applications.  I was able to do it from Abiword and OpenOffice, for example, but could not print an email from Thunderbird directly to .pdf.   You can rest assured that a machine running OSX will be able to read the .ps file easily, and I suspect a Windows machine can handle it but I don't know exactly how it will do it. I don't have a Windows machine to test this on.  On my Mac, I double-clicked the file and it did a temporary conversion to .pdf in the Preview application, and when closing the file you have the option of saving the changes to complete the conversion to .pdf or discarding changes to keep it as a .ps.  Either way I could read the file just fine.

---

### Post by lduplantie on 2008-01-11
Thank you.

Windows will not open a .ps file. Or at least, Windows does not have a .ps file viewer.

---

### Post by djtansey on 2008-02-24
It saves it, by default, to ~/PDF (/home/username/PDF) when you use cups-pdf. If you use OO.org's exporter, then it saves to a different place (since it uses a different system.)

-David

---

### Post by noynac on 2008-02-25
> **lduplantie said:**
> Is there a way to select the file name under which the print job will be saved as a PDF file (pint to file option will save it as a PostScript file) Thanks
There is not a way to select a file name. However, you can edit the file /etc/cups/cups-pdf.conf and change the "Key: Label" setting to 1. A job-id will then be added to every document.

---

### Post by lduplantie on 2008-02-25
Thanks. Looks like it will have to be a two step process.

---

### Post by noynac on 2008-02-25
Please delete

---

