---
title: "[SOLVED] Open Office"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Majorflam on 2008-01-23
I have created a CV using Word. It all looks fine in Word, and I believe that most employers will be viewing it in Word.

Unfortunately, when it is viewed in Open Office, all the font sizes and the general layout appears differently. I'd prefer to use Open Office and would appreciate if anyone could give me some tips on how to create a CV in OO that will maintain it's layout when employers view it in Word.

Thanks in advance for any advice offered.

---

### Post by emarkd on 2008-01-23
I may be showing my ignorance on this subject because I'm not sure what you mean by CV?  However, my general experience is that documents created in OpenOffice and saved as .doc usually display just fine in Word, but the reverse is not always the case.

If I were you, I'd clean up my document so it looked like I wanted it in OpenOffice, then save it as a .doc and then open it in Word and see how it looks.

---

### Post by Wim Sturkenboom on 2008-01-23
Save as PDF might be an option.

@emarkd
CV is more than likely curriculum vitae (I hope I spelled it correctly)

---

### Post by mikewhatever on 2008-01-23
> **Majorflam said:**
> I have created a CV using Word. It all looks fine in Word, and I believe that most employers will be viewing it in Word.

Unfortunately, when it is viewed in Open Office, all the font sizes and the general layout appears differently. I'd prefer to use Open Office and would appreciate if anyone could give me some tips on how to create a CV in OO that will maintain it's layout when employers view it in Word.

Thanks in advance for any advice offered.

Unfortunately, OO abilities to support MS formats are not bulletproof, thanks to the latter. There is no way you can create a document in OO and ensure it would look the same in MS office. The best option is to convert your CV to pdf which is a common format, so people would have no problems viewing it.

PS: (CV=Curriculum Vitae):)

---

### Post by emarkd on 2008-01-23
Curriculum Vitae!  Ah!  I didn't even consider that one.  :oops:

Thanks to everyone for setting me straight.

---

### Post by Majorflam on 2008-01-23
> **emarkd said:**
> I may be showing my ignorance on this subject because I'm not sure what you mean by CV?  However, my general experience is that documents created in OpenOffice and saved as .doc usually display just fine in Word, but the reverse is not always the case.

If I were you, I'd clean up my document so it looked like I wanted it in OpenOffice, then save it as a .doc and then open it in Word and see how it looks.

Thanks for the advice, and a CV is a curriculum vitae. Have never applied for a job!!?

---

### Post by stchman on 2008-01-23
> **Majorflam said:**
> I have created a CV using Word. It all looks fine in Word, and I believe that most employers will be viewing it in Word.

Unfortunately, when it is viewed in Open Office, all the font sizes and the general layout appears differently. I'd prefer to use Open Office and would appreciate if anyone could give me some tips on how to create a CV in OO that will maintain it's layout when employers view it in Word.

Thanks in advance for any advice offered.

Create your CV in Openoffice Writer and see how it looks when you open it in M$ Word.

---

### Post by mister_pink on 2008-01-23
Ill echo the other comments - save it as a pdf, its so easy to do and means it cant get messed up. As a bonus it looks a bit more professional too!

---

### Post by Majorflam on 2008-01-23
OK, I'm liking the pdf option as it does indeed look more professional.

One drawback: The .doc version is 4 pages and roughly 90kb in size. The pdf is exporting at nearly 600kb.

How can I reduce filesize? It's purely text with no images whatsoever, and I can't see export options to reduce filesize. :confused:

---

### Post by bwtranch on 2008-01-23
PDF at 600K, figures. I really can't stand Adobe. Almost as bad as MS. Well that's another rant for another time. See if you can zip the file with gzip cd to the dir and type:

gzip filename

I would usually recommend tar, but...ya know. You may need sudo before that. It would be funny if they could figure out:

tar.gz2 filename and uncompress it. Now that's someone you would want to work for.:)

---

### Post by macogw on 2008-01-24
> **Majorflam said:**
> 
One drawback: The .doc version is 4 pages and roughly 90kb in size. The pdf is exporting at nearly 600kb.
Wow!  I'm guessing it must have something to do with coming from a word processor.  Maybe try retyping it (or copying and pasting) and saving as .odf first, then exporting the pdf from that?  I know MS's .doc format stores a LOT of extra information about you (like, I've been told by HR people that it's possible for them to get old versions of your resume/CV back out of the current .doc version, yikes!  plus things like even your computer's MAC Address O_O).  To see what's included, try opening a .doc in Word Pad (I think you have to rename the file as .rtf) on Windows some time.  It'll open fine, but you'll see all the extra info they include.

I do my resume in LaTeX (a typesetting language, makes it look very professionally laid-out...LyX is supposed to be a good GUI way of doing LaTeX), but it's only 1 page.  Looking at my 4-page lab report (for the proper length comparison) that I did in LaTeX and "compiled" into a PDF, it's only 49K.  Oddly, my resume is 53K even though it's only one page.  I'm guessing that has to do with the information from the res.cls (a resume "class" or style sheet...tells the LaTeX compiler how to lay everything out...that file is 25K) being included, which would only need to be included once, so it'd probably come out to like 150K max.

---

### Post by hyper_ch on 2008-01-24
do you have a picture in your CV?

---

### Post by Majorflam on 2008-01-24
I don't have any images in the CV, only text. It's strange that it's such a large file, I'll need investigate this extra info theory.

---

### Post by Majorflam on 2008-01-24
Well I've saved in rich text format and viewed with Wordpad and there's no extra info that I can see.

Curiously, I converted into .pdf from .doc in Windows using Macromedia Flash Paper and the file size was 111kb. Clearly it's Open Office's native converter that's causing the trouble.

Does anyone know any alternative converters available for Linux?

---

### Post by Majorflam on 2008-01-24
OK guys, I've solved this.

The original CV was written in Word, and over the years I suppose a load of "invisible" garbage made it's way into the file. I've retyped it in Open Office and then exported as pdf. The pdf file size is now 36kb. The plain text file size is 19kb.

Seeing as the CV looks the exact same as before, I'm considering this another victory for Linux over Windows.

Now, if only I could get that printer driver working... :lolflag:

---

### Post by Joeb454 on 2008-01-24
Glad you sorted that out :) If possible can you mark the thread as solved?

It's in thread tools at the top of the page

---

### Post by Majorflam on 2008-01-24
Done, and many thanks for the help. If it wasn't for this board, I wouldn't be able to use Ubuntu and that would be a real shame.

Thanks again.

---

### Post by ubuntu27 on 2008-01-24
Glad you solved your problem. Expoert as PDF in OpenOffice.Org is a  life saver :)

This is almost unrelated, but I feel the need to evangelize about OO.o

An Interesting Article about OpenOffice.Org:

[What's inside Open Document Format (ODF) ?]("http://www.linux-magazine.com/issues/2007/75/what_s_inside") Did you know they are not merely a text file but a "container"?  Read it at [Linux Pro Magazine's]("http://www.linux-magazine.com") [Issue 75]("http://www.linux-magazine.com/issues/2007/75")

Read it online at
[http://www.linux-magazine.com/issues/2007/75/what_s_inside](http://www.linux-magazine.com/issues/2007/75/what_s_inside)



[OpenOffice.Org tips and tricks]("http://openoffice.blogs.com/")

---

