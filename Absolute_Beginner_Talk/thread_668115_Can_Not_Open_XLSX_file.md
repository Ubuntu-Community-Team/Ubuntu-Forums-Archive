---
title: "Can Not Open XLSX file"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by asiakingtravel on 2008-01-15
Hi everybody,

Can some one hepl me, i can not open the file with xlsx format, which sofware can  i use ?

Thanks,
Nam

---

### Post by K.Mandla on 2008-01-15
Moved to Absolute Beginner Talk.

---

### Post by Joeb454 on 2008-01-15
I thought this earlier, I had the same issue.

Just use Open Office Spreadsheet and navigate to where the file is, and open it. It should open fine, though I don't think you'll be able to save in xlsx format.

Hope this helps

---

### Post by Odd-rationale on 2008-01-15
You can convert the file to ods (OpenDocument spreadsheet) or xls  (Microsoft Excel Spreadsheet) using [http://www.zamzar.com](http://www.zamzar.com)

---

### Post by ephro on 2008-03-10
I found this in Google:

[http://wvarner.blogspot.com/2008/02/microsoft-docx-files-on-ubuntu-gusty.html](http://wvarner.blogspot.com/2008/02/microsoft-docx-files-on-ubuntu-gusty.html)

After following it's advice (but coping all the filters and types from version 1.1 of odf-convert), I'm happily opening Office 2007 files, such as xlsx files in OpenOffice 2.3. No annoying uploading and downloading, or even running any other programs.


Ephro

---

### Post by Andrew.Z on 2008-03-15
> **ephro said:**
> I found this in Google:

[http://wvarner.blogspot.com/2008/02/microsoft-docx-files-on-ubuntu-gusty.html](http://wvarner.blogspot.com/2008/02/microsoft-docx-files-on-ubuntu-gusty.html)

After following it's advice (but coping all the filters and types from version 1.1 of odf-convert), I'm happily opening Office 2007 files, such as xlsx files in OpenOffice 2.3. No annoying uploading and downloading, or even running any other programs.

[odf-converter-integrator](http://katana.oooninja.com/w/odf-converter-integrator)  (chocolate edition) does what is described in that link, but it OCI is easier because you just install a package.

---

### Post by Joeb454 on 2008-03-15
Like I said a couple of months back - just tell OOo to open the file, and it'll do it just fine, though I don't know whether it'll save it back to the same filetype

---

### Post by Andrew.Z on 2008-03-15
The problem is the default OpenOffice.org 2.3 on Ubuntu 7.10 includes an alpha version of the OpenOffice.org 3.0 filter, so many features are missing.  That's the reason for OCI.

---

### Post by javroch on 2008-03-30
I've posted this elsewhere, but I figure it applies regardless. So, I thought I'd post again. I'm not exactly sure why nobody else seems to have tried this, but if you download the odf-converter-x.x-x.oxt file from Novell's website, instead of the rpm, you can install it just as you would in Windows. AND, it will not only allow you to use .docx files it'll also do .xlsx and .pptx files as well. I'll outline the steps for you if you'd like:

Go to Applications > Office and open OpenOffice.org Word Processor
In OpenOffice.org Word Processor go to Tools > Extension Manager...
In Extension Manager click "Add..." and locate the .oxt file.

That's it!

---

### Post by calc on 2008-03-31
I think this (.xlsx) should already work in Ubuntu Hardy and should be somewhat improved for automatically opening other filetypes with the next upload.

---

### Post by bryanagee on 2008-05-19
Also of interest.... gnumeric can load _and_ save .xlsx files. Handy if you don't want clients/colleagues complaining about the older version dialogs.

---

### Post by n8bounds on 2008-06-23
This is much easier, just download a deb and double click to open with gdebi

[http://katana.oooninja.com/w/odf-converter-integrator/download](http://katana.oooninja.com/w/odf-converter-integrator/download)

---

