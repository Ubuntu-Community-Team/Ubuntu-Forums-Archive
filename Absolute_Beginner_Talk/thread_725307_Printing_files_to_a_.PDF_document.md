---
title: "Printing files to a .PDF document"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Airforcefalco on 2008-03-15
Can anyone help me again?

Thank you.

---

### Post by ghost_ryder35 on 2008-03-15
OpenOffice can do it

---

### Post by prshah on 2008-03-15
> **Airforcefalco said:**
> Can anyone help me again?

Thank you.

If you are printing from Open Office then you can just choose File->Export to PDF. Otherwise open System->Administration->Printing, then select "New Printer" and after the wait is over, choose "Print into PDF file" and finish the printer setup.

Then, open whatever you want and print using the PDFPrinter.

Your PDF file will be in your home directory/PDF, eg: /home/someone/PDF (or ~/PDF)

---

### Post by Nepherte on 2008-03-15
Ubuntu 7.10 has a built-in PDF printer. Go to system > administration > printers and choose new printer. There should be an option' print to PDF'. It will install the PDF printer and from then on, you can choose the printer from any application.

edit: as told above.

---

### Post by Airforcefalco on 2008-03-15
It is a x-shockwave-flash object that has a printing option. I wanted a friend to take a look at the file because it is for college and it needs a password but i wanted to show her just a few paragraphs and an image in it.

What is the linux shortcut for copy?

Thanks again

---

### Post by Airforcefalco on 2008-03-15
Ahh thank you. I did set up the printer but i didn't know where it saved it! Thank you guys so much!

---

### Post by Andavane on 2008-03-27
> **Nepherte said:**
> Ubuntu 7.10 has a built-in PDF printer. Go to system > administration > printers and choose new printer. There should be an option' print to PDF'. It will install the PDF printer and from then on, you can choose the printer from any application.

edit: as told above.
Thank you.
Been having more trouble with this than I would have liked.
I didn't see the pdf maker in gutsy in admin>printer>choose new printer in my version.
I installed "cups-pdf" through synaptic, then
went print to print a page
and the progress bar shows it's "doing" it but then it just vanished.
Either it didn't do it, OR
It did it and put it somewhere I-don't-know-where.

Any suggestions?

I really do like to use this program a lot.

John

---

### Post by rkd on 2008-03-27
I don't know anything about cups-pdf, but a quick Google search turned up these pages:

[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml)
[http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/)

On the second of those pages, be sure to read down through all the comments.

I gather from reading those pages that the location where the .pdf file goes is controlled by the "Out" specification in the file cups-pdf.conf, and its default is to put the output into /var/spool/cups-pdf/name, where "name" is your user name.  See all the directions on those pages for more complete information -- it looks like you have to do some file security modifications after the installation to let things work right, so maybe your attempt to create the .pdf file didn't really work if you didn't know to make those adjustments.

It looks like the method described by prshah in post #3, above, requires much less setup, so it might be a good idea to just forget about cups-pdf and do what prshah describes.

---

### Post by Andavane on 2008-03-28
> **rkd said:**
> I don't know anything about cups-pdf, but a quick Google search turned up these pages:

[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml)
[http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/)

On the second of those page.....It looks like the method described by prshah in post #3, above, requires much less setup, so it might be a good idea to just forget about cups-pdf and do what prshah describes.
This has fixed the problem here:
[http://www.stchman.com/pdf_cups.html]("http://www.stchman.com/pdf_cups.html")

prshah's post is fine for matters pertaining to pdf's printed from Open Office

---

### Post by rkd on 2008-03-28
The way I read prshah's post, it describes two methods.  The first works only within Open Office; the second works for printing from any application.  See that "Otherwise at the start of the second sentence?  I think that starts the second method, which I believe works for any application.

I'll admit that I've not tried it, but taking the writing at face value, you first create a PDF printer in System/Administration/Printing, then when printing, in the print dialog, choose that PDF printer as the "printer" to which you send the output.  Seems pretty simple to me, but maybe there is something I'm overlooking.

---

### Post by Andavane on 2008-03-28
> **rkd said:**
> The way I read prshah's post, it describes two methods.  The first works only within Open Office; the second works for printing from any application.  See that "Otherwise" at the start of the second sentence?  I think that starts the second method, which I believe works for any application.

I'll admit that I've not tried it, but taking the writing at face value, you first create a PDF printer in System/Administration/Printing, then when printing, in the print dialog, choose that PDF printer as the "printer" to which you send the output.  Seems pretty simple to me, but maybe there is something I'm overlooking.
Yes I see what you mean. The 'otherwise'. As I remember, it didn't seem to work, but there again I may well have not followed the process through. Indeed as printer does need to be installed, and it's "other" then "generic" then "postscript" and that fixes it.
Knowing me I may well have missed that.
Thanks for pointing it out.

PS: I seem to remember that on Feisty Fawn this was never a problem.

---

