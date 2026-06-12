---
title: "Print Server Printing"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-12
Ok, I have a print server/NAS (Level one FNS-1000) and a canon lbp-1120 printer. I have the printer working fine (thanks to some very helpful tutorials), but now I would like to run it from the print server if I can. Is this possible? If so, How?


Thanks very much in advance. :)

---

### Post by adaptr on 2006-12-12
This may depend on many factors, such as:
[LIST]
[*]What is the interface to the printer that the print server provides ? Does it do IPP, or HP-style print serving, or LPR, or what ?
[*]If the print server only supports RAW printing (as may often be the case in something "designed" for Windows), can you get Linux to work with the printer in RAW mode ?
[*]What kind of interfaces does the _printer_ provide ? Does it come with a Windows-only USB driver, or does it also support IPP, LPR, RAW, or full PostScript?
[*]Can you get the combination of those three working together reliably?
[/LIST]
Simply put, the answer to the last question depends for a large part on how good the support for the printer is for standards like LPR or PostScript - if the **printer** supports PostScript then almost anything you want is possible.

---

### Post by Jussi01 on 2006-12-12
Its one of those nasty CAPT jobs... see [here]("http://www.canon.co.uk/For_Home/Product_Finder/Printers/Laser_Beam/LBP_1120/index.asp")

I actually dont know what it supports...

---

### Post by adaptr on 2006-12-12
From the Product Specifications on that page (you might have clicked on that yourself), it supports absolutely nothing besides the Canon proprietary language.
Not even Macs are supported - oh boy.

The very first thing one does is head over to linuxprinting.org and browse for salvation - or even desperate measures.

This yields

[http://linuxprinting.org/show_printer.cgi?recnum=Canon-LBP-1120](http://linuxprinting.org/show_printer.cgi?recnum=Canon-LBP-1120)

which tells you that there is a solution which **mostly** works.
Since the whole job is a bloody Winprinter anyway, you will *always* have to print RAW from Linux.

As long as the print server supports this, it will work exactly as well as it does now.

Why did you show me the specs for the printer, when you were inquiring about the print **server **?

---

### Post by Jussi01 on 2006-12-12
> **adaptr said:**
> 
Why did you show me the specs for the printer, when you were inquiring about the print **server **?


Firstly thanks very much for your help

I really appreciate the time some people put into helping others :KS 

To answer the question, I wanted to answer your question - and I thought that website did...

> # What kind of interfaces does the printer provide ? Does it come with a Windows-only USB driver, or does it also support IPP, LPR, RAW, or full PostScript?

---

