---
title: "Can Evince print in landscape?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by falcon15500 on 2006-10-11
I was trying to print out a PDF the other day and noted that it was in landscape orientation.  Scanning through the print options in Evince, I was unable to find an option to change the print orientation???

Is this true?  Or am I just not finding it?


falc

---

### Post by gdi2k on 2006-11-08
I'm having this issue too - I have a landscape document, but when I try to print, it prints portrait (with half the content off the page). 

I noticed in the "Advanced" settings of the my printing properties, there is a "N-up Orientation" dropdown, where Landscape can be selected, but it makes no difference, the print still comes out incorrectly. 

Any ideas? 

GDI

---

### Post by jonah1980 on 2006-11-30
yeah same problem here

---

### Post by WolfJay_83 on 2006-12-10
I cant find an option for landscape.  That might be something that needs to be filed as a bug.

If you need to print a pdf document in landscape now, you can open a terminal, cd to the directory where the pdf file is, and type

lpr -o landscape filename.pdf

explenation:
lpr           -print to default printer
-o            -give a specific setting to the printer
-filename.pdf -the name of the file your printing

There are other pdf viewers that can be easily installed and used in ubuntu.  Open synaptic and search for xpdf, kpdf, or acroread. (for adobe acrobat reader, you might need the extra repositories enabled.)

Its too bad evince seems to be missing landscape print, because it integrates best with the ubuntu desktop (xpdf is ugly, kpdf is a kde program, and acroread is non-free)

---

### Post by jonah1980 on 2006-12-11
ok cool i don't mind submitting the bug... i'll go do it now on gnome.org

---

### Post by jonah1980 on 2006-12-11
ok here's the bug if you guys wanna add to it:

[http://bugzilla.gnome.org/show_bug.cgi?id=384726](http://bugzilla.gnome.org/show_bug.cgi?id=384726)

---

### Post by aperomsik on 2006-12-20
evince 0.70 (now in feisty) seems to solve this problem. They managed to confuse me with the new page setup dialog, which has portrait and landscape options. Turns out that usually you DON'T want to set landscape, unless your paper is sideways in the printer. For normal usage, load the PDF, hit Print, and it Does The Right Thing (tm).

I used prevu to backport 0.70 to edgy. I wonder if it's worth an official update. I had to update gnome-icon-theme as well.

---

