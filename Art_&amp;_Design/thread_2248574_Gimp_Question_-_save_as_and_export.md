---
title: "Gimp Question - save as and export"
date: 2014-10-15
forum: Art &amp; Design
---

### Post by michael-piziak on 2014-10-15
I upgraded to Ubuntu 14.x lts and now the version of gimp only lets me save a file as .jpg if I export the file (use to be I could just do a save as)

Is this normal ?

---

### Post by Dennis N on 2014-10-15
> Is this normal ?
No, I don't think so. On mine File > Export > Select File Type by Extension has over 40 image types to select from.

---

### Post by ajgreeny on 2014-10-15
But you do have to use the "Export" option, not simply save, as used to be possible, so "Yes" it is now normal unless you want to save as an .xcf file.

If you open an existing file and edit it you can then use the "Overwrite" option in the File menu.

Seems strange having to save files that way at first, and I have no idea why it is necessary, rather than a direct "Save" option, but you very soon get used to doing it and it becomes second nature.

---

### Post by SeijiSensei on 2014-10-15
The GIMP developers chose to split the File Save and File Export functions in version 2.8.  I've never really understood why this happened, but saving a file now means saving in GIMP's native XCF format.  To save in any other format you need to use Export.

---

### Post by michael-piziak on 2014-10-15
I don't think you understand my question.  On the previous version of Gimp one could do a file "save as" and save as a .jpg file

---

### Post by michael-piziak on 2014-10-15
Thank you, you answered my question perfectly.

---

### Post by ofnuts on 2014-10-16
> **SeijiSensei said:**
> The GIMP developers chose to split the File Save and File Export functions in version 2.8.  I've never really understood why this happened, but saving a file now means saving in GIMP's native XCF format.  To save in any other format you need to use Export.

Because "Saving" as JPG doesn't save much... Assusme you have worked up an image with 20 layers... then "Save" as JPG... since the image is saved you can just exit now.... and lose all your layers (and complex selections, paths...). When saving as XCF you don't lose anything (except the undo history).

Gimp has for a long time provided a "Save a copy" function but noone used it (still there, and still a very useful thing to save an intermediate version while you work).

As a mod in several Gimp forums since 2.6 times, I can witness that the anguish of people who now have to use "Export" to produce a JPG is nothing compared to the distress of people wondering how they could recover all their layers.

---

### Post by SeijiSensei on 2014-10-16
I suppose.  I found the 2.6 interface more consistent with most other types of programs, where you choose "File > Save," then select the output format from a drop-down box or by adding the appropriate extension to the new file name.  Mainstream office programs like MS Office, Open/LibreOffice, and Gnumeric, all use this method.  Usually they throw up a warning dialog that your file will be saved in a different format, and some loss of information may occur.

---

### Post by Thee on 2014-10-16
Use **Export as **to save to a different image format.
Use **Save as **to save to GIMP native format, with layers.

---

### Post by michael-piziak on 2014-10-16
I find the way it works now to be more of a hastle.  I just opened a jpg image and did a quick change and went to "save" and it wouldn't save itself to jpg format - one still has to export.

Also, with "save as," one can't even choose to change the format to .jpg - the list of file formats is short and doesn't have jpg

I will try to use this version for a while and see if I can get use to it.  If it continues to annoy me I'll go back to the previous version of Gimp.

---

### Post by ajgreeny on 2014-10-16
> **michael-piziak said:**
> I find the way it works now to be more of a hastle.  I just opened a jpg image and did a quick change and went to "save" and it wouldn't save itself to jpg format - one still has to export.

Also, with "save as," one can't even choose to change the format to .jpg - the list of file formats is short and doesn't have jpg

I will try to use this version for a while and see if I can get use to it.  If it continues to annoy me I'll go back to the previous version of Gimp.
No. That is where you can choose the "Overwrite" option without going to the export, as I mentioned in post #3.

You are making it more difficult than it really is.

---

### Post by ofnuts on 2014-10-17
> **SeijiSensei said:**
> I suppose.  I found the 2.6 interface more consistent with most other types of programs, where you choose "File > Save," then select the output format from a drop-down box or by adding the appropriate extension to the new file name.  Mainstream office programs like MS Office, Open/LibreOffice, and Gnumeric, all use this method.  Usually they throw up a warning dialog that your file will be saved in a different format, and some loss of information may occur.

It's a matter of "function" in the other format. When you save a .XLS as .ODS or vice-versa, you don't lose much. When you "save" a .XCF as a JPG, it a bit like if you saved your .XLS/ODS as a PDF...  (which coincidentally is in "File/Export" in LibreOfficce).

---

