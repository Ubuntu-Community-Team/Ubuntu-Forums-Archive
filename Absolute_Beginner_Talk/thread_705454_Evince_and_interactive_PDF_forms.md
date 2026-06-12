---
title: "Evince and interactive PDF forms"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by bob12564 on 2008-02-23
The documentation for Evince/Gnome clearly states that Evince has save and print support for PDF forms.  

I downloaded an IRS tax form and sure enough I was able to open it in Evince and tab to the input fields and type information.  However, when I save the file, all I get when I reopen it is the original PDF file without the text I filled in.

I then decided to experiment by creating a form in Open Office Writer and exporting it as a PDF form.  Nice feature!  I then opened it in Evince and again I was able to enter text.  I tried save but once again when I reopened the file I got the original file without my text.

So the question is one of clarification.  When the Gnome documentation states that Evince has "save" support for PDF forms, does that include the text that's filled into the forms?  I get the impression (although I haven't tried it) that Adobe Reader does it.  There doesn't seem to be much point for the IRS to make tax forms available as PDF forms if you can't fill them out and save them.  I presume the intention is to allow you to complete the form and then file electronically.

Thanks!

---

### Post by mali2297 on 2008-02-24
Have you tried *printing to file*?

You can also see if it works with [Adobe  Reader for Linux]("http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html").

---

### Post by bob12564 on 2008-03-21
I'll try to print to file.  Just printing doesn't work.  Print to file has been suggested in another thread I found.  According to that thread, the Gnome documentation is incorrect and Evince cannot save or print the text fields as stated.  Adobe Acrobat for Windows behaves as expected but I haven't tried the Linux version.  I've read other posts that say it has problems.

Thanks for the reply.

---

### Post by anco on 2008-05-29
This is more than annoying... I tried acrobat reader on Hardy, but same problem. Acrobat reader comes up with a pop up window that it can't save the filled form. only printing is allowed! How annoying! On windows it works some what better, the form I need to fill in has an email button which sents the data, but even that doesn't work on ubuntu with evolution. It triggers only microsoft mailsystem. 

I made screencopies as an image to be able to sent the filled in forms by email. This is a major lack of feature. How can they make pdf's which can't be saved? I don't get it.

---

### Post by e_labranche on 2008-06-04
On windows, mac or linux, interactive files can't be saved. It's just the way it is. For you to save it, you need to print to file.

I use adobe acrobat reader on my ubuntu, and I can do exactly the same with the files, like I can on windows, including email the file, print etc.

---

### Post by kaibob on 2008-06-05
The about screen in Evince indicates that it uses poppler 0.6.4. The developer indicates on the following page that Evince needs poppler 0.7.0 in order to save filled-in forms. 

[http://bugzilla.gnome.org/show_bug.cgi?id=480668](http://bugzilla.gnome.org/show_bug.cgi?id=480668)

I downloaded the IRS PDF form and could fill it in but not save it.

---

