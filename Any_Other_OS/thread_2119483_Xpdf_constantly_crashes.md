---
title: "Xpdf constantly crashes"
date: 2013-02-24
forum: Any Other OS
---

### Post by RaHorakhty on 2013-02-24
I can't get xpdf to load a pdf file on Unbuntu 12!  The app shutdowns down when I try to open a pdf.  I checked[ foolabs]("http://www.foolabs.com/xpdf/links.html") for an update.  any ideas?  Looks like I'll have to stick to the windows version for now....

---

### Post by andrew.46 on 2013-02-26
Is there an error message if you run xpdf from the commandline? Looks like a few bugreports around for the xpdf crash, a few different culprits involved though...

---

### Post by RaHorakhty on 2013-03-01
I don't use the cmdline to load pdf files.  I use the GUI to load files...file/open.  The app craps out as soon as I try loading any pdf!  where can I find a log file for xpdf?  Do you think I should try loading it through the cmdline to see if it generates an error?

---

### Post by andrew.46 on 2013-03-01
> **RaHorakhty said:**
>   Do you think I should try loading it through the cmdline to see if it generates an error?

Yes, the bug reports I saw all generated an error when run directly from the commandline.

---

### Post by BBQdave on 2013-03-01
> **RaHorakhty said:**
> I can't get xpdf to load a pdf file on Unbuntu 12!

If you use FireFox, a nice alternative is the pdf viewer that is loaded by default in FF19.

---

### Post by RaHorakhty on 2013-03-02
Great idea Andrew.  Here's what the mess looks like....

```

***** MediaBox = ll:0,0 ur:595,792
***** CropBox = ll:0,0 ur:595,792
***** Rotate = 0
q
cm 1 0 0 1 72 36
RG 0 0 0
m 6.6 475.2
l 165 475.2
S
rg 0 0 0
re 0 181.3 487 2
f
BT
Tf /F9 20
  font: tag=F9 name='Helvetica-Bold' 20
Td 0 634
Tc 0
Tj (Advanced Bash-Scripting Guide)
Tf /F9 17
  font: tag=F9 name='Helvetica-Bold' 17
Td 0 -73.8
Tj (An in-depth exploration of the art of shell scripting)
Tf /F9 14
  font: tag=F9 name='Helvetica-Bold' 14
Td 0 -30.6
Tj (Mendel Cooper)
Tf /F0 11
  font: tag=F0 name='Courier' 11
Td 0 -53.4
Tj (<thegrendel.abs@gmail.com>)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Td 0 -26.4
Tj (6.2)
Td 0 -26.4
Tj (17 March 2010)
Tf /F5 11
  font: tag=F5 name='Times-Bold' 11
Td 1.432 -27.832
Tj (Revision History)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Td 0 -16.065
Tj (Revision 6.0)
Td 156.988 0
Tj (23 Mar 2009)
Td 159.198 0
Tj (Revised by: mc)
Td -316.186 -16.065
Tj ('THIMBLEBERRY' release: Major Update.)
Td 0 -16.065
Tj (Revision 6.1)
Td 156.988 0
Tj (30 Sep 2009)
Td 159.198 0
Tj (Revised by: mc)
Td -316.186 -16.065
Tj ('BUFFALOBERRY' release: Minor Update.)
Td 0 -16.065
Tj (Revision 6.2)
Td 156.988 0
Tj (17 Mar 2010)
Td 159.198 0
Tj (Revised by: mc)
Td -316.186 -16.065
Tj ('ROWANBERRY' release)
Td -1.432 -27.832
Tj (This tutorial assumes no previous knowledge of scripting or programming, but progresses rapidly toward an)
Td 0 -13.2
Tj (intermediate/advanced level of instruction)
Tf /F6 11
  font: tag=F6 name='Times-Italic' 11
Tj ( . . . all the while sneaking in little nuggets of UNIX&#65533; wisdom and)
Td 0 -13.2
Tj (lore)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Tj (. It serves as a textbook, a manual for self-study, and a reference and source of knowledge on shell)
Td 0 -13.2
Tj (scripting techniques. The exercises and heavily-commented examples invite active reader participation, under)
Td 0 -13.2
Tj (the premise that )
Tf /F1 11
  font: tag=F1 name='Courier-Bold' 11
Tj (the only way to really learn scripting is to write scripts)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Tj (.)
Td 0 -26.4
Tj (This book is suitable for classroom use as a general introduction to programming concepts.)
Tf /F9 20
  font: tag=F9 name='Helvetica-Bold' 20
Td 0 -37.4
Tj (Dedication)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Td 0 -28.2
Tj (For Anita, the source of all the magic)
ET
Q
***** Annotations
***** page 1 *****
***** MediaBox = ll:0,0 ur:595,792
***** CropBox = ll:0,0 ur:595,792
***** Rotate = 0
q
cm 1 0 0 1 72 36
RG 0 0 0
m 6.6 475.2
l 165 475.2
S
rg 0 0 0
re 0 181.3 487 2
f
BT
Tf /F9 20
  font: tag=F9 name='Helvetica-Bold' 20
Td 0 634
Tc 0
Tj (Advanced Bash-Scripting Guide)
Tf /F9 17
  font: tag=F9 name='Helvetica-Bold' 17
Td 0 -73.8
Tj (An in-depth exploration of the art of shell scripting)
Tf /F9 14
  font: tag=F9 name='Helvetica-Bold' 14
Td 0 -30.6
Tj (Mendel Cooper)
Tf /F0 11
  font: tag=F0 name='Courier' 11
Td 0 -53.4
Tj (<thegrendel.abs@gmail.com>)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Td 0 -26.4
Tj (6.2)
Td 0 -26.4
Tj (17 March 2010)
Tf /F5 11
  font: tag=F5 name='Times-Bold' 11
Td 1.432 -27.832
Tj (Revision History)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Td 0 -16.065
Tj (Revision 6.0)
Td 156.988 0
Tj (23 Mar 2009)
Td 159.198 0
Tj (Revised by: mc)
Td -316.186 -16.065
Tj ('THIMBLEBERRY' release: Major Update.)
Td 0 -16.065
Tj (Revision 6.1)
Td 156.988 0
Tj (30 Sep 2009)
Td 159.198 0
Tj (Revised by: mc)
Td -316.186 -16.065
Tj ('BUFFALOBERRY' release: Minor Update.)
Td 0 -16.065
Tj (Revision 6.2)
Td 156.988 0
Tj (17 Mar 2010)
Td 159.198 0
Tj (Revised by: mc)
Td -316.186 -16.065
Tj ('ROWANBERRY' release)
Td -1.432 -27.832
Tj (This tutorial assumes no previous knowledge of scripting or programming, but progresses rapidly toward an)
Td 0 -13.2
Tj (intermediate/advanced level of instruction)
Tf /F6 11
  font: tag=F6 name='Times-Italic' 11
Tj ( . . . all the while sneaking in little nuggets of UNIX&#65533; wisdom and)
Td 0 -13.2
Tj (lore)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Tj (. It serves as a textbook, a manual for self-study, and a reference and source of knowledge on shell)
Td 0 -13.2
Tj (scripting techniques. The exercises and heavily-commented examples invite active reader participation, under)
Td 0 -13.2
Tj (the premise that )
Tf /F1 11
  font: tag=F1 name='Courier-Bold' 11
Tj (the only way to really learn scripting is to write scripts)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Tj (.)
Td 0 -26.4
Tj (This book is suitable for classroom use as a general introduction to programming concepts.)
Tf /F9 20
  font: tag=F9 name='Helvetica-Bold' 20
Td 0 -37.4
Tj (Dedication)
Tf /F4 11
  font: tag=F4 name='Times-Roman' 11
Td 0 -28.2
Tj (For Anita, the source of all the magic)
ET
Q
***** Annotations
Segmentation fault

```

What? lol

---

### Post by RaHorakhty on 2013-03-02
ill check it out.  I'm looking around for a pdf file viewer with special utilities....

---

### Post by andrew.46 on 2013-03-02
> **RaHorakhty said:**
> Great idea Andrew.  Here's what the mess looks like....

```

[...]
Segmentation fault

```



Hmmm... not terribly helpful although it can be seen that xpdf has a seg fault. The behaviour of your copy is unusual, what is normally seen when run from the commandline is that xpdf loads the file in gui and gives any error messages in the Terminal. Perhaps it is time to search out a replacement for xpdf?

---

### Post by sudodus on 2013-03-02
> **RaHorakhty said:**
> I can't get xpdf to load a pdf file on Unbuntu 12!  The app shutdowns down when I try to open a pdf.  I checked[ foolabs]("http://www.foolabs.com/xpdf/links.html") for an update.  any ideas?  Looks like I'll have to stick to the windows version for now....
You wrote that you run Unbuntu 12. Do you mean Ubuntu 12.04 LTS o 12.10? I wouldn't say that is [OtherOS] ;-)

The default pdf viewer is ***evince*** in Ubuntu. Will there be a difference if you try to show that file with evince instead of xpdf? My experience is that evince is much better, and I don't know if they share libraries.

---

### Post by RaHorakhty on 2013-03-04
xpdf is a great freeware app.  I don't think there's a utility as featureful as xpdf available. What would you recommend?  The pdf viewer in FF19 is meant for viewing pdf files. I'm looking for a pdf editor/viewer combined.  I know I can load it through a VM....trying to avoid the hassel.

---

### Post by sudodus on 2013-03-04
> **RaHorakhty said:**
> xpdf is a great freeware app.  I don't think there's a utility as featureful as xpdf available. What would you recommend?  The pdf viewer in FF19 is meant for viewing pdf files. I'm looking for a pdf editor/viewer combined.  I know I can load it through a VM....trying to avoid the hassel.

1. Will ***evince*** show the file that xpdf cannot show? It should be installed as the default pdf viewer in your Ubuntu.

2. What do you want to do? General editing of pdf files or just making notes or filling in a form?

***- Xournal*** is good for making notes or filling in forms on pdf files. You can install it from the repositories and try it.
```
sudo apt-get install xournal
```

***- Gimp*** can import pdf files and do even more (but only on one page each time).

It is typical in linux, that there are different tools for different tasks, no big general 'I can do everything tool'.

---

