---
title: "How to print multiple pages onto one sheet of paper?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by woland on 2006-11-10
I have a lot of pages to print from a Power Point presentation converted into  a PDF file format. Printing them one page per sheet, or even 2 pages per sheet (two sides) would be a waste of paper and ink, and also a lot of pages to carry. 
I want to print 4 pages from the PDF file to each side of the sheet, 8 pages onto one sheet of paper.
In Windoze I had this handled by a printer driver feature (Cannon i550).
Acrobat reader, doesn't offer this feature, and it simply doesn't work in evince.

Is there any other program or way to print multiple pages onto one sheet?

I used to run windoze in vmware in order to print pages this way, but vmware stopped working in Edgy and I didn't yet figured out how to make it work yet.

---

### Post by ahaslam on 2006-11-10
You can do it in kde, using the printer settings. I'm not keen on kde, so I installed kdebase (minimal kde environment) mainly to use this feature in gnome. I recommend that you install with aptitude, so that it's dependencies can be easily removed if you don't like it.

Once it's installed use this command to launch the printer settings: 
kcmshell printers

Here's a screenshot of it in action under gnome:
[ATTACH]19123[/ATTACH]

Hope that helps.

Tony.

---

### Post by woland on 2006-11-11
Thanks Tony!
It didn't work with evince, but it worked with kpdf.

---

### Post by ahaslam on 2006-11-11
No probs mate, glad to help.
I've never used evince, but if may work after a reboot. For some reason the settings don't always work system-wide straight away :-? 

Tony.

---

