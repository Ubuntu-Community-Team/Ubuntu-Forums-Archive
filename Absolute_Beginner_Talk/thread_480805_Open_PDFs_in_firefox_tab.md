---
title: "Open PDFs in firefox tab?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-06-21
I've been reading a lot of websites lately with pdfs, and having to download them and open them in a seperate program (window) is beginning to get at me. Is there any way to open them in a firefox tab, like any other webpage?

---

### Post by wormser on 2007-06-21
I tried to change the default app for pdf files to Firefox and that did not work.  Does anybody else have an idea?

---

### Post by h0ax on 2007-06-21
My pdf's open in firefox --> 
Firefox2 and evince pdf reader

---

### Post by Mothinator on 2007-06-22
It involves installing a plugin for firefox called mozplugger. I installed the latest version from source: [Mozplugger]("http://mozplugger.mozdev.org/"). You can also install mozplugger and evince (an open source PDF viewer) from the repositories.

If you install from the repos you may have to configure a file as described in this how to:
[ HOWTO: Embed PDFs with Evince in Mozilla/Firefox]("http://ubuntuforums.org/showthread.php?t=25685")

I didn't have to reconfigure any text files. It just worked after I installed it.

---

### Post by wormser on 2007-06-22
I did not have to edit the text file.  It just worked.  I looked at the file and saw the line was already there.

Thanks!

---

### Post by riutaro on 2007-06-23
Hi,

I have just installed MozPlugger 1.7 and it makes PDF downloads open in Firefox tabs (according to this [HOWTO](http://ubuntuforums.org/showthread.php?t=25685)).  This is great!

I have one question, though.  How can I change the program with which to open the PDFs?  Currently it is Acrobat Reader that opens PDFs, even after I have changed the default "Open WIth" to Evince in file properties tab in Nautilus.

---

### Post by Golyadkin on 2007-06-23
I run [this extension ]("https://addons.mozilla.org/en-US/firefox/addon/636")which works fine for me, it allows me to have more control over what I do with a PDF. Some 20MB+ PDFs you don't want to open in a tab :)

---

### Post by Brucevdk on 2007-06-23
> **riutaro said:**
> I have one question, though.  How can I change the program with which to open the PDFs?  Currently it is Acrobat Reader that opens PDFs, even after I have changed the default "Open WIth" to Evince in file properties tab in Nautilus.

It looks to me like mozplugger checks for Acrobat Reader before using Evince, at least that's what it looks like in */etc/mozpluggerrc*. The easiest way to get it to use Evince is to remove Acrobat Reader, if that's not an option it might be possible to remove all lines with *ACROREAD()* from */etc/mozpluggerrc*.

---

### Post by riutaro on 2007-06-23
> **Brucevdk said:**
> The easiest way to get it to use Evince is to remove Acrobat Reader (...)

Not being a software collector, I am all for getting rid of Acrobat Reader if Evince works just as fine; my query — how does Evince fare regarding multilingual support?  I remember, in Windows, I had to download so many support patches to enable AcroReader to display my PDF files correctly.  I don't believe I tend to download files many oddities but I have more than a fair share of linguistic variety: glossaries in some 20 languages.

---

