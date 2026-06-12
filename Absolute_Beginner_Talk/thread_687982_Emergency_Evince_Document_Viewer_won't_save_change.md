---
title: "Emergency: Evince Document Viewer won't save changes"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2008-02-04
My dad wanted me to get my tax forms done tonight so we could send them in for the fafsa, and I downloaded the forms online and started editing it with the Evince Document Viewer. AFAIK, this is the standard that ships with ubuntu. I filled everything out on my forums, but when I click save it saves a copy without the changes made to it, that is, the original document without my info on it.
I tried printing it, but the printer won't connect, it would connect painlessly in Feisty, but in Gutsy it has issues, is there any way I can install the Feisty printing system and print this tonight?
My father has always scoffed at linux, and I can't tell him I couldn't get this to work. Is there any other pdf viewer I can use?

---

### Post by y-lee on 2008-02-04
I wasn't aware on could edit pdfs with Evince Document Viewer. I think it is just for viewing PDFs. I have 3 PDF viewers installed, adobes, Kpdf and Kghostview but i doubt they would allow ya to edit and save either. However see [ PDF Editor]("http://www.linux.com/feature/113907") for a method that might be able to do that.

As for your printer problem, i don't know. sorry.

---

### Post by Bubba64 on 2008-02-04
Open the down load in open office if it is not a PDF file, probably you need to down load again into open office. As far as I know you can't edit a PDF and have it saved without some custom program. I tried to find a program a while back but had no luck. I am not an expert on this though, you might try to google or searching on this forum with your printers name and Gutsy for instruction on how to get it working just make sure you get valid information

---

### Post by bob12564 on 2008-02-24
I have the exact same problem.

To all responders...we're not talking about editing the PDF file.  We are talking about PDF forms which are sometimes called interactive PDFs.  The Gnome 2.20 documentation states that Evince has the ability to handle PDF forms and to save or print them.  What is not clear in the documentation is whether it will also save and print the text that is entered into the form fields.  I would assume it should because there's no point in having a PDF form if you can't save and print the text you enter into the form fields.

You can also create your own PDF forms via Open Office Writer.  Just use the forms toolbar to add a few text boxes and then export to PDF.  You'll even see a check box for "forms" in one of the setup panels.  Then open the PDF file in Evince and type away!  Try printing or saving.

The IRS in the USA is posting all tax forms as PDF forms.  The idea is that you can type your data onto the forms and get a clean print to mail to them or even fax/email to your accountant or even file electronically.  Anyone who wants to try it can go to [www.irs.gov](www.irs.gov) and look for the 1040 form as an example.  Let us know what happens.

---

### Post by y-lee on 2008-02-24
> The IRS in the USA is posting all tax forms as PDF forms. The idea is that you can type your data onto the forms and get a clean print to mail to them or even fax/email to your accountant or even file electronically. Anyone who wants to try it can go to [www.irs.gov](www.irs.gov) and look for the 1040 form as an example. Let us know what happens.

Ok I downloaded one of The irs's taxs forms and I couldn't fill in the form at all in Evince 0.5.2 using Dapper, but when I open it in Adobe reader, I got the message below:

> This form has document rights applied to it. these rights allow anyone completing this form, with the free Adobe Reader, to save their filled-in form locally

 I could both fill in the forms and save my changes :)

Note: Adobe Reader 8.1.1 is available in [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") for Ubuntu 7.10  

See [To install Adobe Reader]("https://help.ubuntu.com/community/AcrobatHowTo")

---

### Post by bob12564 on 2008-02-24
The current version of Evince running under Gutsy does allow you to fill in the PDF form.  

Thanks for testing the IRS form with Adobe Acrobat.  I'd like to stay with open source products and Evince is nice in many ways, but ultimately if you can't get your work done using the open source products than the commercial software is the only option.

---

### Post by y-lee on 2008-02-24
> The current version of Evince running under Gutsy does allow you to fill in the PDF form.


Well that is good to know, I'm planning on upgrading to Gusty or hardy sometime soon. trying to hold out till hardy is released actually. lol

---

### Post by deadrabbit on 2008-03-17
I ran into the same thing with my 1040 form - Evince didn't save the filled fields. However, in Gutsy you can "Print to File" as a PDF, and that PDF will contain the filled fields. I guess it's too late for you, but if anyone else happens to google "1040 evince" and come up with this thread like I did, I hope it helps.

---

### Post by bruce89 on 2008-03-17
This has been a deficiancy in poppler, see [http://bugzilla.gnome.org/show_bug.cgi?id=480668](http://bugzilla.gnome.org/show_bug.cgi?id=480668)

---

