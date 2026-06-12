---
title: "URGENT: Printer Canon BJC-2010"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Famicommander on 2008-04-14
I've only got an hour to get this thing set up, so please help me.

I'm running Xubuntu 7.10 and I have to get this Canon BJC-2010 printer working fast. 

Here's what I've done so far:
1. Applications>Settings>Printing>New Printer
2. Found my printer on a list and selected the Canon BJC-2010 - CUPS+Gutenprint v5.0.1 Simplified driver

I've never set up a printer before, so I assumed that was all I needed to do. When I try to print things, however, they just go to a queue and nothing happens. I don't know where to go from here.

---

### Post by Famicommander on 2008-04-14
Come on, guys. I know we're supposed to be patient here, but I have to get this thing set up before I leave. It's my grandmother's printer, and she needs it set up before I go to track practice.

---

### Post by kellemes on 2008-04-14
Have you tried selecting another printer in the list? Like BJC-2000?
As I understand it the hardware is the same..
[http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-2010]("http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-2010")

---

### Post by stchman on 2008-04-14
That printer is supported mostly under Linux.

[http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-2010](http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-2010)

Make sure you select the gnutenprint driver.

Also make sure you select Letter over A4.  Since Ubuntu is made overseas and A4 is the standard that causes the printer to stall.

I find that after you install the printer to use CUPS web tool.

[http://localhost:631](http://localhost:631)

and select the proper paper type.

---

### Post by Famicommander on 2008-04-14
> **stchman said:**
> That printer is supported mostly under Linux.

[http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-2010](http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-2010)

Make sure you select the gnutenprint driver.

Also make sure you select Letter over A4.  Since Ubuntu is made overseas and A4 is the standard that causes the printer to stall.

I find that after you install the printer to use CUPS web tool.

[http://localhost:631](http://localhost:631)

and select the proper paper type.
It detects my printer and everything is set up, but when I try to print a test page it says "parallel port busy; will retry in 3 seconds"

When I try to print things in OpenOffice or AbiWord, nothing happens. It's exactly the same as it was when I started.

---

### Post by kellemes on 2008-04-14
parallel?
User needs to be added to lp group.

---

### Post by Famicommander on 2008-04-14
> **kellemes said:**
> parallel?
User needs to be added to lp group.
How do I do that?

---

### Post by Famicommander on 2008-04-14
I've got 8 minutes to get this thing running, guys. Please, please help me out.

---

### Post by kellemes on 2008-04-15
> **Famicommander said:**
> I've got 8 minutes to get this thing running, guys. Please, please help me out.

O man, I hope you got it fixed on time, being on GMT+1 I had to go get some sleep ;-)

To answer your question.
```
sudo adduser <username> lp
```

---

