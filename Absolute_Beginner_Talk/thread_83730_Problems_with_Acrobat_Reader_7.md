---
title: "Problems with Acrobat Reader 7"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by thinhlegolas on 2005-10-29
I managed to install Acrobat Reader 7 successfully following the README file. However whenever i call the program from /usr/local/Adobe/AcrobatReader7.0/bin/acroread, it will just show the splash screen and then disappear with no error message :(

---

### Post by nitricacid on 2005-10-29
I just use openOffice.org

---

### Post by sas on 2005-10-29
If you click on a PDF or open one in your web browser then evince should just start up, it's a nice PDF viewer.

I'm not sure what your specific problem is to be honest, there's not much to go on.

---

### Post by thinhlegolas on 2005-10-30
Solved this... i use apt-get install acroread to install Acrobat Reader 5, then i uninstall it and install Reader 7 again... and it works this time... i guess when I installed it the first time there were some packages missing

I want Acrobat Reader 7 since it's the only program that can display all pdf files correctly :)

---

### Post by nitricacid on 2005-10-30
[QUOTE=thinhlegolas]

I want Acrobat Reader 7 since it's the only program that can display all pdf files correctly :)[/QUOTE]


Never had any problems with OpenOffice.org so far...
Then again, most of the PDF files i download.

---

### Post by sas on 2005-10-31
[QUOTE=thinhlegolas]I want Acrobat Reader 7 since it's the only program that can display all pdf files correctly :)[/QUOTE]

It will probably be helpful if you report files which don't work in evince/xpdf here: [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)

evince does currently have problems with semi-transparent/gradient images in PDFs iirc, hopefully they'll be fixed for dapper.

---

### Post by Luffield on 2005-10-31
[QUOTE=nitricacid]Never had any problems with OpenOffice.org so far...
Then again, most of the PDF files i download.[/QUOTE]I tried to use OOo 1.9.129 to open PDF files and couldn't do it (drag and drop, file->open, neither worked). Can you please tell me how to do it?

I'm not very happy with Evince, mainly becaue I can't control the zoom accurately.

---

