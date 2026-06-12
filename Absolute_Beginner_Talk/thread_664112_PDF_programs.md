---
title: "PDF programs"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by lsearcey on 2008-01-10
I have many PDF files that have signature fields which are sign with an electronic signature pad.  Is there a Linux compatible program that can do this?  In Windows I used Adobe Acrobat 7

Thank You

---

### Post by NovaAesa on 2008-01-10
Are you wanting to sign the PDFs, or just view ones that have already been signed?

---

### Post by RomeReactor on 2008-01-10
Hi. I don't know if Evince (the included PDF reader in Ubuntu) supports this, but [Xpdf]("http://www.foolabs.com/xpdf/") claims to support reading encrypted files; search for it in Add/Remove (Applications->Add/Remove) or Synaptic (System->Administration->Synaptic). Otherwise, you might want to use [Acrobat 7]("ftp://ftp.uni-koeln.de/www/acrobat-reader/unix/AdobeReader_enu-7.0.9-1.i386.tar.gz") or [Acrobat 8]("http://www.adobe.com/products/acrobat/readstep2_allversions.html") (for Acrobat 8, select the .tar.gz or, preferably, the .deb package).

---

### Post by lsearcey on 2008-01-10
I'm wanting to be able to view and sign them.  Will Adobe Acrobat 7 or 8 work on Ubuntu?

---

### Post by Rocket2DMn on 2008-01-10
Those links give you Adobe Reader.  At least in Windows, you can sign forms and save a data file, but not the pdf itself.  I imagine it works similarly in Ubuntu (and linux in general), I think I shall try it myself.

---

### Post by lsearcey on 2008-01-10
i would like to be able to edit and sign PDF files can that be done with XPDF or some other program within Ubuntu?

---

### Post by crjackson on 2008-01-10
Install it and let US know...

---

### Post by FuturePilot on 2008-01-10
Acrobat Reader is in the Medibuntu repository
You can add it by opening a terminal (Applications>Accessories>Terminal) and entering this
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install acroread acroread-escript acroread-plugins mozilla-acroread
```

---

### Post by jrusso2 on 2008-01-10
Here is a list of all of them.  I am not sure which does what you want.

[http://en.wikipedia.org/wiki/List_of_PDF_software](http://en.wikipedia.org/wiki/List_of_PDF_software)

---

### Post by lsearcey on 2008-04-20
I tried PDFEdit and since I'm new it seems very complicated compared to Adobe Acrobat Pro 7.  I'll keep trying to learn it but it would be nice to have Adobe Acrobat Pro 7 Linux version.

---

