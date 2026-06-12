---
title: "iWork to Open Office"
date: 2010-04-14
forum: Apple Hardware Users
---

### Post by dcheifer on 2010-04-14
I'm working on switching from OS X to Ubuntu, and I have a question about file conversion.  I used iWork quite a bit on my Mac, and have a very large number of important .pages documents that I really can't afford to lose access to.  Is there any easy way to convert them all into a form that I can use with Open Office, or will I have to export them one by one using pages?

---

### Post by atoinajoolie on 2010-04-14
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]i don't really no what open office does but i was told that if i don't have office mac i should download it... however, i have purchased iwork so i am wondering weather i need to bother with either,


[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by anurse on 2010-04-14
Check pages to see if you can export your documents to either open office file format (odt) or a neutral format that both can open and edit. Doc will work as long as your files are generally text. Unfortunately, this is a one at a time solution.

---

### Post by dcheifer on 2010-04-14
Yeah, I know I can export to .doc, but I've been using Pages for about the last eight continuous years of school, so I have a TON of documents I'd rather not lose.  I'm just hoping that by some chance there's a less tedious way to do this.

---

### Post by dcheifer on 2010-04-14
Oh, and if you have iWork and Open Office both give you word processing, presentation software, and spreadsheets.  If you have iWork and you are happy with it, you don't need Open Office.  But realize that if you use iWork and ever decide to switch to another OS, you will have to change all of the file types, because iWork's files are not compatible with any other application.

---

### Post by linuxopjemac on 2010-04-15
> But realize that if you use iWork and ever decide to switch to another OS, you will have to change all of the file types, because iWork's files are not compatible with any other application.

Thanks to Apple....

---

### Post by dcheifer on 2010-04-15
> **linuxopjemac said:**
> Thanks to Apple....

Tell me about it!  This kind of thing is why I've started to dislike Apple.  Most of what Apple makes only works with other things Apple makes.  They're so obsessed with creating a very specific kind of user experience that they make their products inflexible and incompatible with anything else.

---

### Post by oswaldkelso on 2010-04-15
I do work for a small charity and we have many appleworks docs. I have been slowly but surly converting all our documentation to odf. Ironically this is done by exporting to a M$ format!! As apple wants to ensure it's apps open in M$ office. 

Then I open in open office. The conversion is a pain but a one time only pain.

As a charity we have to preserve our accounts and minutes for at least 7 years. ODF, plain text, and PDF is our solution. Getting there can be a chore but then it's "simples" to quote the famous TV add I've never seen. Apple is becoming a PITA. I loved their hardware but since switching to Intel they're idea of freedom is worse than M$.

Never before has an example of digital lock-in been so perfectly executed. (up-grade or die) 

They're still running OSX, but using neo-office to manage their documentation. Firefox and Seamonkey for browsing with thunder-bird for e-mail. VLC for video, etc.

[http://www.opensourcemac.org/](http://www.opensourcemac.org/)

Of course if I had my way they'd just run Debian but you can't win them all. :)

---

### Post by computermacgyver on 2011-04-09
I just received a pages file by email and found it is actually a zip file (same as .docx and .odt). Inside the zip file, was a folder QuickLook with a PDF view of the document called Preview.pdf . This allowed me to quickly view the document without needing iWorks.

Also within the zip file is a index.xml file, which contained the document and all the formatting. I was able again to easily read the document by simply stripping all the xml tags from the file with sed (e.g. cat index.xml | sed 's/<[^>]*>//g'  on a terminal). This gave me a no-formatting version of the document.

None of these is really a full or long-term solution, for which building a proper Pages->OpenOffice extension is probably the way to go. In the meantime, for a small number of documents that do not contain sensitive information online file conversion sites may work. I haven't tried [http://www.zamzar.com/](http://www.zamzar.com/) but it says it supports Pages.

---

### Post by JeffRheault on 2011-04-10
Automator is the way to go!

---

### Post by netgifted on 2011-11-28
Just open the .pages document with archive manager. There is a folder called "Quick look" inside there is a PDF file containing your iWork document. It's not the best solution but it works fine. Pages is a really nice word processor and what I usually do is saving my documents in both .pages and .doc format. 
People that criticize Apple never used a Mac on a regular basis. I love ubuntu and it rocks on my Macbook Air inside a VMWare Fusion machine. It's my fastest Ubuntu machine (I am using it right now)

---

