---
title: "printing problem with Virginia Department of Taxation form"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-03-30
I am having a problem with getting a Virginia Department of Taxation tax form to print correctly.

[http://www.tax.virginia.gov/taxforms/Individual/Income%20Tax/2007/760.pdf](http://www.tax.virginia.gov/taxforms/Individual/Income%20Tax/2007/760.pdf)

It is an individual tax form for 2007 and I am attempting to print it to my HP laserjet 2100 printer.

The form looks fine on screen in Adobe Reader but when I print the form, for instance, the header in the "Your first name" block prints as "Your  rst name, i.e. leaving out the F & I.  There are also many other instance of this same type of print problem on the form.

I can print tax forms from the IRS website, with no problem, that I can see.

Can anyone give me a hint as to what may be the cause of this problem ?

Is it possible that this is just a problem that the Virginia Tax site has in that it my not be compatible with the Linux, Firefox, world ?

Thanks.

---

### Post by lswest on 2008-03-30
Hmm, the only thing i can think of is:
a) Unsupported font (which shouldn't apply to a PDF)

b) bad export OF the PDF (but then it should be in the file too)

c) bent head of the ink cartridge in the printer (less likely, as it seems to only be occurring with this document)

d) running out of ink/the colour of the text is too light

e) if possible, try it in a different printer, or have someone try to print it, and if the error persists, then it has to be a problem with the file, or with Linux's way of handling the print job.

Not sure how likely any of the examples would be, but, as i said before, those are the only things that come to mind.

---

### Post by wpshooter on 2008-03-30
Thanks for your reply.

I am just wondering that if it might have to do with the level of graphics on the Virginia form as opposed to the less graphics on the IRS forms ?  And in combination with the amount of memory that the printer has, 4mb I think.  Wonder if the printer needs more memory.  But you would think that if printer was lacking in memory that print information would be spooled/held somehow until memory was available ??

Thanks.

---

### Post by wpshooter on 2008-03-31
I printed this Virginia Department of Taxation tax form on my work (M/S Windows) computer to an HP1200 series local printer and guess what, NO problem.

I sure wish someone could come up with some printer drivers for Ubuntu/Linux that would work as consistently as the windows based drivers for the HP printers.

Thanks.

---

### Post by wpshooter on 2008-04-03
As a followup on this problems with forms printing incorrectly from the Virginia Department of Taxation website, I have discovered that this problem has to be either a problem with a bad download of the Adobe Reader for Linux program or an actual bug in the Adobe Reader for Linux program itself because when I brought some copies of the print files that were missing characters on my home computer to work and then opened them on my M/S Windows version of Adobe Acrobat all of the missing character were sudden displayed properly again.

I am calling Adobe this morning to see if they can discover the root cause of this problem.

Thanks.

---

### Post by wpshooter on 2008-05-10
I tried this again on a new installation of Hardy final release this morning and it appears that all of the messages, faxes and bug reports that I have spent to the Virginia Department of Taxation and to the Canonical Launchpad bug report have finally paid off.  I don't know who, but apparently the right party final got the message.  The form 760 now prints without any missing characters.

The squeaky wheel gets the grease !!!

---

