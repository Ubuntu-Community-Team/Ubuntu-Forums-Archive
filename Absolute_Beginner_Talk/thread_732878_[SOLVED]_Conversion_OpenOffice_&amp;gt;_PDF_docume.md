---
title: "[SOLVED] Conversion OpenOffice &amp;gt; PDF document"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-23
This should be interesting: when I convert an OpenOffice word.doc into a PDF format, the hyphens and inverted commas mysteriously disappear in the PDF version. No difference if I open the PDF doc with the "native" ubuntu PFD or through Acrobat 8. Hyphens and inverted commas are not there...
Any idea?

---

### Post by BandD on 2008-03-23
I had this exact same problem.  After a tip in the OOo forums someone suggested that the font being used in OpenOffice is not actually installed on my system.  And sure enough, the default font was something like 'Roman' rather than 'Times New Roman'.  'Roman' wasn't an actual font that was installed on my system.  Because of this, the PDF didn't know how to handle the smart quotes and other non-standard punctuation.

So the fix (I'm assuming you are trying to convert a document from Writer to PDF)...

Open up OOo Writer and go to the tools menu.  Then go down to Options.  Once the options menu pops up, click the "+" next to Openoffice.org Writer and click the 'Basic Fonts' menu item.  Then change the Default Font to 'Times New Roman' or any other font that is ACTUALLY installed on your system.  (see attached picture) 

That should do the trick.  If it works, mark this baby SOLVED!

Regards,

Dustin

---

### Post by al.adab on 2008-03-23
Thanks - I'm in the middle of something and cannot try to convert now to test it - one thing though, maybe you know about this as well: open office word is acting rather weird at the moment, like showing patches of color around toolbars and open office related window I open (see screenshot in attachment). What shall I do? Looks like a bug...

---

### Post by al.adab on 2008-03-23
I'm afraid it didn't work. I used OO before in combination with PDF, and never had this kind of trouble. Here's the screenshot of my OO settings (as it was before I posted this thread, actually). It'd be great if a solution was found to this. Thanks.
PS: as for the patches of color, I turned off the Nvidia driver, and it's now ok.

---

### Post by al.adab on 2008-03-25
Just noticed that the conversion NEW open office word.doc into PFD works fine. "Old" word.docs (i.e., imported from Windows) do not perfectly convert into PDF (the doc in my initial thread was in fact an "old" one).
Any idea?

---

### Post by Hagar Delest on 2008-03-26
As said, I'm quite sure it's a font issue too. Make sure that all the fonts used in your doc are installed, especially if it comes from Windows. Is the msttcorefonts package installed?

To check if the fonts used in a documents are indeed installed, use that extension: [TestFonts]("http://extensions.services.openoffice.org/project/TestFonts").

---

