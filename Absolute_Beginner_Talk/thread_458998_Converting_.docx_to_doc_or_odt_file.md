---
title: "Converting .docx to doc or odt file"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by anuraggautam on 2007-05-30
I want to open some .docx ( Microsoft Word 2007 file) file in the ubuntu linux........for that what to do.can i convert .docx to .doc ...........or to .odt ....so that i can open the files.......

Reply Fast guys !

---

### Post by Seisen on 2007-05-30
I don't know if the .docx extension will open in OpenOffice but you can try opening it up using OpenOffice. Then all you would have to do is save it in a .odt extension if it will let you open the file.

---

### Post by christhemonkey on 2007-05-30
If not you can always read the text of the .docx by using this:
[http://docx-converter.com/](http://docx-converter.com/)

Or to any sort of document like this:
[http://www.zamzar.com/](http://www.zamzar.com/)

---

### Post by anuraggautam on 2007-05-30
its not  working......:(

---

### Post by Seisen on 2007-05-30
What's not working, OpenOffice.

---

### Post by BHelts on 2007-05-30
you can try this.  i think you'd have to run it through wine though.

[DocX Converter Utility]("http://www.softpedia.com/get/Windows-Widgets/System-Utilities/Docx-Converter.shtml")

it interfaces with the website the first poster put up.

---

### Post by anuraggautam on 2007-05-30
openoffice is not able to open .docx files.......i have to convert firstly.......it may be like that docx is not supported by ubuntu due to its newness.....:)

---

### Post by ruscoe on 2007-05-30
The docx format is actually an archive that you can extract in Ubuntu. It used to be the case that you could open a normal doc file from within it, sans formatting, but I think that's changed now and all you get is a messy pile of XML files.

[http://joeanderson.co.uk/blog/2006/01/26/dismantling-a-docx/](http://joeanderson.co.uk/blog/2006/01/26/dismantling-a-docx/)

Ask people to save as .doc. Worked for me.

---

### Post by Seisen on 2007-05-30
Thats why I said I didn't know if it would work or not.

---

### Post by anuraggautam on 2007-05-30
@ruscoe  so how to open these files........XML files ...how can i make it readable

---

### Post by ruscoe on 2007-05-30
> **anuraggautam said:**
> @ruscoe  so how to open these files........XML files ...how can i make it readable
You don't.

A converter might work, I haven't tried them, but the best method is asking people who send you files to send them in a nicer format.

---

### Post by BHelts on 2007-05-30
> openoffice is not able to open .docx files.......i have to convert firstly.......it may be like that docx is not supported by ubuntu due to its newness.....

unfortunately, docx is not compatible with anything except office2007.  it's microsoft's answer to openoffice and staroffice.  it won't be long, i don't think so anyway, before the openoffice guys and gals get OOo up to speed. 
in the meantime, have the user of office2007 change their default document type from .docx / .xlsx back to .doc / .xls.  this can be done by going to the "Pearl".  Click on the "Office Button" then at the bottom of the list click on "Word Options".  In the resulting dialog box click on "Save".  Change the option "Save files in this format" to .doc- office 97 - office 2003 Document or something to that effect.  best of luck.

---

### Post by mlentink on 2007-05-30
Seeing as how DOCX is Microsoft's "Open"XML 'standard', you might want to ask the person who sent you this file to resend it in a really open standard like Open Document. 

You could change the filename to .ZIP and then use an unzipper to uppack the files inside it, but I doubt you'll be able to reproduce what was originally intended.

---

