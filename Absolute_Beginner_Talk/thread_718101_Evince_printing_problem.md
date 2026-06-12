---
title: "Evince printing problem"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2008-03-07
Hello,
Any suggetions on how to get Evince to print my PDF files?
I am running Ubuntu 7.10
HPprinter
When I click PRINT I get nothing, when I click on PRINT PREVIEW I get the error message:
"Unhandled MIME type: text/plain"

Kinda strange that it wont print plain text isn't it??

Thanks

---

### Post by davarino on 2008-03-08
Are you saying that when you click Print you do not get a print dialog window?

I assume that you can print from other applications than Evince.

---

### Post by mali2297 on 2008-03-08
Have you tried several different PDF files?

---

### Post by halfB on 2008-03-13
Me Too!!
What I mean is I am also unable to get Evince to print.  I run 7.10 on 2 different machines.  Neither one will print any pdfs.  They both can print other documents to multiple printers without trouble.  
This is very frustrating. 
halfB

---

### Post by BartInTN on 2008-03-25
Same problem here.  When I select print, the options dialog pops up.  If I hit print, nothing happens.  If I hit print preview, then I get the error message:
Unhandled MIME type: &#8220;text/plain&#8221;

I have to move the pdf files to a Windows box and print them to my HP network printer from there.  This happens only on some pdfs, I can otherewise print just fine from Ubuntu, including from Evince.

---

### Post by mali2297 on 2008-03-25
Have you tried [Adobe PDF Reader]("http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html")?

---

### Post by BartInTN on 2008-03-25
Got it to successfully print by running Evince as root... must be a permissions problem.

---

### Post by stchman on 2008-03-25
> **3pinner said:**
> Hello,
Any suggetions on how to get Evince to print my PDF files?
I am running Ubuntu 7.10
HPprinter
When I click PRINT I get nothing, when I click on PRINT PREVIEW I get the error message:
"Unhandled MIME type: text/plain"

Kinda strange that it wont print plain text isn't it??

Thanks

I had this problem.  I went to the CUPS web interface.

```
localhost:631
```

I selected my printer in question and selected Letter instead of A4.  Since Ubuntu was written by Canonical in South Africa they use A4 paper and here in the US we use letter.  That fixed my problem.  Seems if you change the paper size in System--->Administration---Printing it still does not take.  Use the web interface.

---

### Post by sleon on 2008-03-31
Go to File | Print | Page Setup tab and make sure that "Only print:" is set to "All Sheets".  I got the same Unhandled MIME type: "text/plain" error while printing single page pdfs (it was set to even sheets).  Haven't had a problem since (gutsy btw).

---

### Post by EBAR on 2008-03-31
I have this exact same problem. My printer works perfectly for every application other than Evince. But when I run Evince as root, it prints the document.

Is there a permanent solution to this problem?

---

### Post by Mariano Oliveto on 2008-04-07
> **sleon said:**
> Go to File | Print | Page Setup tab and make sure that "Only print:" is set to "All Sheets".  I got the same Unhandled MIME type: "text/plain" error while printing single page pdfs (it was set to even sheets).  Haven't had a problem since (gutsy btw).

I've been having the same problem and this fixed it. I'm wondering if this is a bug...

Thanks sleon for the solution :D

---

