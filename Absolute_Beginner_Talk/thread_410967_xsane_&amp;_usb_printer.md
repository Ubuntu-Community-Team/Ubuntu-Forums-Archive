---
title: "xsane &amp; usb printer"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-04-16
I have a HP LJ 1000 printer that works fine in Edgy but I don't know the command for it in xsane.  xsane works fine with the printer I have attached to lpt1 using the command "lpr" in the xsane printer command box. What do I put on this line to get xsane to see my HP usb printer?

I am trying to add the printer in the xsane setup section, copy tab, which is the only place I can find to do this.

---

### Post by leibowitz on 2007-04-25
Just a little search on the website would bring you to a full list of printers. Just choose yours.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=printer&titlesearch=Titres](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=printer&titlesearch=Titres)

Note: Xsane is for scanning only. So I suppose you have a Multi function printer. Maybe an HP. And if you are using Feisty Ubuntu 7.04 then you will just need to install hpoj.

```
sudo apt-get install hpoj

```
Reference: [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

---

### Post by simohell on 2007-05-25
For printing a direct copy with xsane you need to add your printer to xsane's list of printers.

As I understand you found that it is done at:

Preferences --> Setup --> Copy

How to use the command line printing command lpr (which works for myself) is as follows

```
lpr -P printer -#4 filename
```

Therefor to get the printer working in xsane you need to define  the command "lpr" and with option "-P" give your printer's name as it is listed in the Printers list. The "Name" Field appears to be for the Printer selection list within xsane.The number of copies ("-#") is automatic from xsane interface. You can also define the printing resolution in dpi.

For myself the important settings are:
```

Name: Stylus-C66
Command: lpr -P Stylus-C64
Copy number option: -#

```

---

### Post by simohell on 2007-05-25
> 
You can also define the printing resolution in dpi.


Ok. Maybe it is the scanning-resolution one defines here. Probably printing resolution comes from the Printer default settings...

---

### Post by Trismegister on 2007-06-10
I did find it necessary to uncheck the default option to create a postscript file for my Epson inkjet to work with XSane Copy

---

