---
title: "Scribus and Printing?"
date: 2007-02-12
forum: Art &amp; Design
---

### Post by shane2peru on 2007-02-12
Wow, just started using this awesome program just a week ago.  It is incredibly nice layout program for desktop publishing.  I do wish it came with a bunch of little graphics to use, but you can't get it all for the price!  Anyway, it won't print.  I have an HP 1310 printer and every time I try to print something directly, it sends it to the printer, I click on the little printer in the icon tray to see what is going on, because it claims to be printing, but nothing happens.  When I double click the little printer icon, it opens my printer, and says there is a document for print, but that it is stopped?  I don't stop it, so why is it stopped?  I end up clicking on cancel document, because it never does anything?  Anyone have any ideas?  I'm using Edgy 6.10.

Shane

---

### Post by Unterseeboot_234 on 2007-02-15
You should be using Scribus-ng from the repositories, not the "official" Synaptic download. Look for the "-ng" in the Advanced download of Synaptic. That might fix your problem. I, myself, have yet to connect my *buntu box to the printer as it is networked to a group of XP boxes. So, as a natural choice whenever I wanted to have a hard copy I was **Export **-ing my page layout from Scribus as a .pdf, copy it over the network to the XP box, open it there and print. Maybe you can do the same thing. Try printing any .pdf. If that works, try Export and print .pdf.

---

### Post by shane2peru on 2007-02-15
Thank you for the reply!  I do have the Scribus-ng installed.  I started with the other then searched the forums and realized this was the older version and installed the newer one.  Also, as for the PDF method, that is the way I have been getting around direct printing.  I export to PDF then open it in Adobe Reader (has better printing options) and print.  I would just like to avoid that step and be able to directly print, modify and print again.  Without having to open the PDF that I exported Print, modify, then re-export, then re-open then Print.  :(  Few to many steps for working on a project over and over.  Thanks though.

Shane

---

### Post by Unterseeboot_234 on 2007-02-15
We learn by trying to help. I went to Scribus FAQ ... Printing??? It turns out Scribus formats PostScript Level2, they have seen problems with HP printers and not just with Scribus but also with other Layout programs such as Quark, ImageReady and recommends looking at CUPS -- Common Unix Printing System.

I next looked at Synaptic about CUPS. Ubuntu has configured several GNOME GUI packages that work with CUPS. I still think you can print directly from Scribus.

1. Investigate your Printer, can the driver handle PS-Level2? HP is one of the good companies, they support Linux. Do you have their driver?
2. Then we need to look through CUPS, Scribus suggests CUPS can be misconfigured for a B/W print out. CUPS allows you to configure a driver and give the driver a name.

 [**CUPS -- Common Unix Printing System**]("http://www.cups.org/doc-1.1/sum.html")

======== edit

I also did a search on the *buntu forums for "printing". I think it's important to see what information the OS *THINKS* is the printer's attributes.

**[hptoolbox]("http://www.ubuntuforums.org/showthread.php?t=298993")**

---

### Post by shane2peru on 2007-02-15
> **Unterseeboot_234 said:**
> We learn by trying to help. I went to Scribus FAQ ... Printing??? It turns out Scribus formats PostScript Level2, they have seen problems with HP printers and not just with Scribus but also with other Layout programs such as Quark, ImageReady and recommends looking at CUPS -- Common Unix Printing System.

I next looked at Synaptic about CUPS. Ubuntu has configured several GNOME GUI packages that work with CUPS. I still think you can print directly from Scribus.

1. Investigate your Printer, can the driver handle PS-Level2? HP is one of the good companies, they support Linux. Do you have their driver?
2. Then we need to look through CUPS, Scribus suggests CUPS can be misconfigured for a B/W print out. CUPS allows you to configure a driver and give the driver a name.

 [**CUPS -- Common Unix Printing System**]("http://www.cups.org/doc-1.1/sum.html")

======== edit

I also did a search on the *buntu forums for "printing". I think it's important to see what information the OS *THINKS* is the printer's attributes.

**[hptoolbox]("http://www.ubuntuforums.org/showthread.php?t=298993")**

ok, this is a bit over my head.  I checked and when I installed my printer I remember being very happy that HP had drivers for Linux.  I used the suggested driver HIPJS (or something like that).  I also have hp-toolbox installed, that was the first time I have seen that before, really neat little program.  I don't quite understand the two questions.  > 1. Investigate your Printer, can the driver handle PS-Level2? HP is one of the good companies, they support Linux. Do you have their driver?  What is PS-Level2?  How do I find out if my printer prints that?  

> 2. Then we need to look through CUPS, Scribus suggests CUPS can be misconfigured for a B/W print out. CUPS allows you to configure a driver and give the driver a name.
  My CUPS says it is configured to print at Normal Color 600dpi.  

Thanks for the help!

Shane

Oh, my printer is an HP1315 PSC  - it is nothing grand, just a low end printer.  So I don't think it does any of that ps-level2 printing stuff.  But I really don't know.

---

### Post by Unterseeboot_234 on 2007-02-16
OK, I wished that I had a direct answer for you but I don't have your particular printer. A few observations though:

Scribus has PS2 -- or, Postscript Level 2 -- available when you go to print as a selection option. 

However, HP is using their software that mimics Postscript. (Postscript was a plain-text page description language invented by Adobe to make the front-end(s) of graphics independent from output machines).

linuxprinting.org was SUPPOSED to be the central repository for printer drivers. Something wrong with their Home Page ... I have to cross-click to get to linuxprinting.org web information by visiting linux-foundation.org. (Google found the linux-foundation). Here is the direct link to your printer.

Your printer is listed as acceptable, mostly works, and we know that because you can print out PDF docs.

[**HP PSC1315**]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1315")

They have MailList and forums directly available for printing issues with various printing machines. I will watch this thread. Let us know what you find.

Scribus is a great project which I hope they detail into a real "be-all" program. It isn't as interactive as Quark was, it's more like the old PageMaker, and Scribus has yet to define all the color-palletes needed for the various needs of commercial printing. Scribus loathes Ubuntu because the *buntu users were overloading the project with too many newbie questions about typesetting, fonts, that sort of thing.

---

