---
title: "double sided printing (duplex) of pdf files"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-07-27
Which pdf reading program supports double sided printing (duplex) well ?

I am using Feisty and Gutsy but evince of both don't support double sided printing, although gedit support it well.

How can I print a pdf file using double sided option?

---

### Post by freesitebuilder on 2007-07-27
Mine is done through my printer driver - my Canon isn't supported, so I use TurboPrint third party driver. With that, I can choose File > Print (in Evince), and choose the Page Setup tab to change to double-sided printing.

What printer are you using?

---

### Post by sundol on 2007-07-28
> **freesitebuilder said:**
> Mine is done through my printer driver - my Canon isn't supported, so I use TurboPrint third party driver. With that, I can choose File > Print (in Evince), and choose the Page Setup tab to change to double-sided printing.

What printer are you using?

I am using Ricoh imagio Neo C325it.
I tried TurboPrint after seeing your message but it didn't support my printer.

---

### Post by ramjet_1953 on 2007-07-28
Of course, if your printer has a duplexer, double-sided printing is a function of the printer, itself.

However, if you want to print double-sided on a printer that doesn't have a duplexer, Adobe Reader has a Sub-Set option in the print menu to print All pages, Odd pages, or Even pages.

I use this feature all of the time for double sided printing, as all you have to do is print odd pages first, then re-insert the printed pages and print the even pages on the other side.

Regards,
Roger :cool:

---

### Post by sundol on 2007-07-29
The printer that I am using supports duplex.

gedit(the default text editer) print double sided one well, as I wrote at the first posting.

However, evince, xpdf, and kpdf doesn't.

Also, the printer was a shared one so that I cannot print the odd and even one, in turn.

---

### Post by guyg on 2008-01-05
I have the HP LaserJet P2015d, which supports duplex printing. I'm using the HP driver (HPLIP). Evince doesn't print duplex, but xpdf does.

---

### Post by vussvillem on 2008-02-21
I'm stuck on a same problem here. I have to use network shared printer and Open Office Writer has no problem printing double sided whereas Evince, Acroread nor Xpdf fail to print duplex.

This problem has already come up in Ubuntu forum as well:
[http://ubuntuforums.org/archive/index.php/t-294626.html](http://ubuntuforums.org/archive/index.php/t-294626.html)

There seems to be a well known bug for a long time. Bug that anybody does not deal with although duplex printing of pdf's is something that some people do for everyday purposes.

There seems to be a temporary workaround for Kubuntu users :
[https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/54154](https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/54154)

---

### Post by alainjackson on 2008-03-28
I had exactly the same issue, trying to print PDFs on my duplex HP LaserJet 2200D, over USB, from my IBM laptop. 

Evince has an option under printer properties to select two-sided printing, but it doesn't let you choose that option.

I've just installed the latest version of Acrocread, 8.1.2,  (the debian package) from Adobe's site.   It's printer properties dialog DOES let me select duplex printing and it does work. 

Hope that helps.

---

