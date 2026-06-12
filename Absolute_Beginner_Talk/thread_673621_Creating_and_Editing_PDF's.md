---
title: "Creating and Editing PDF's"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by green_earth on 2008-01-20
Greetings to all Ubuntuians,

Recently I installed the cups-pdf printer driver... seems to work fine. Also, viewing/reading PDF's in the Evince Document Viewer is fine with a few tweaks to the toolbar (to make me feel at home). However, I've been using Acrobat professional since version 4.0 (I think it was about 1999). I really miss being able to have more control over printing from any program. I'm a little surprised there hasn't been more activity in this area since the cups-pdf driver exists - hasn't there been an expansion on that work to make it more similar to the acrobat distiller? I'd really like to be able to have a dialog box letting me choose a name and a location for my print jobs instead of the ~/pdf folder and whatever the name ends up being at the time of creation.

I could be wrong, but isn't every PDF driver out there on any platform (besides adobe of course) using some implementation of ghostscript? There are several decent PDF creating engines on the windows platform which use ghostscript I believe, and they give you good control similar to distiller.

Anything with more bells and whistles on Linux?

Also, are there any tools for editing PDF's? For example: adding pages, cropping pages, re-arranging pages, and so forth? 

I know several programs offer in-program control over the creation of PDF's (such as openoffice, scribus, Xara, and so on) but I'd really like a full-powered creation and edit capabilities to really be able to leave windows for good (I think I'm about 50% there now).

Thanks for your insights...

---

### Post by Squizz on 2008-01-20
Have you tried Foxit?

I hear that it's available on Linux now.

Scribus and Kpdf do more editing though I think.

---

### Post by Rhubarb on 2008-01-20
Try **pdfedit** in the ubuntu repositories:
------------------------------------------------------------

[I]Editor for manipulating PDF documents
Complete editing of pdf documents is made possible with PDFedit. You
can change either raw pdf objects (for advanced users) or use
predefined gui functions. Functions can be easily added as everything
is based on a scripts.

Scripting is used to a great extent in editor and almost anything can
be scripted, it is possible to create own scripts or plugins.

 Homepage: [http://pdfedit.petricek.net/](http://pdfedit.petricek.net/)[/I]

---

### Post by green_earth on 2008-01-21
Squizz -thanks for your reply. I looked into both Foxit and Kpdf - both are only "readers". Foxit software does offer some editing and creation tools for windows only. I've played around with Scribus a little now, and it does import PDF, but treats them more like an object that I can't seem to deal with like an image (i.e. shift around in a frame or crop).

Rhubarb - thanks for the tip, I've downloaded pdfedit now, and although its geared more for folks familiar with code/scripting, I think it may help me out a little. Its very rudimentary compared to some of the windows products to someone who is used to having lots of gui driven tools - but still, its open source and free!  It doesn't help me with the "creation" side of PDF. But it is better than nothing! I'm really amazed at how much work programmers put into these projects and place their code out there for others to use and modify. With that in mind I've nothing to complain about...

Still searching for that full featured "print to pdf" tool...

---

### Post by smartboyathome on 2008-01-21
You can use OpenOffice.org Writer to create PDF documents. Use File > Export to PDF. Remember to also save it as an ODT document so you can edit it later and export it again easily.

---

### Post by kbless7 on 2008-01-21
I just installed adobe reader 8 on gutsy. There is a .deb file you can download from the website. If they do that for the free version, I'm sure they would it for the pro version that you would have to buy.

---

### Post by green_earth on 2008-01-24
smartboyathome, kbless7:

Thanks for your thoughts. I'm well aware of openoffice's pdf creation abilities - and I'm better off for it. My interest in this thread origination is more along the lines of application independent pdf creation (say from webpages and other programs) but even more specifically the ability to nativly work with pdf's and add/delete pages, croping, and so forth. Because on windows/mac adobe acrobat pro (and a few other third-party programs like foxit) give you such control. So, I can create one single pdf document with files from writer, calc, gimp, or whatever else. I know now its a pipe dream for the present time. But I'm sure it will come along eventually - pdfedit is the best I've found but is a LONG way from being easy to use for boneheads like me. Also, adobe DOES NOT offer anything but reader for any OS excepting windows/mac, at any price. That does not surprise me. On kbless7's reply I downloaded and installed reader 8. Looks and acts just like the windows version. However, on my five year old HP laptop it does run much slower than Evince. Thanks again for your replys...

---

### Post by dedmonds on 2008-03-03
For what it's worth, for application-independent PDF file creation, I print to file to create a PostScript file (filename.ps, for example) then use ps2pdf from the terminal to convert the PostScript file to PDF (ps2pdf filename.ps). I do this quite a bit for saving websites for future reference. This does not address your editing wishes though.

---

