---
title: "Browser says XML document errors"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by marioub on 2008-03-14
My multifunction Epson Stylus CX4800 seems to install just fine and printing works fine, but when I try to scan, I just get black and white with no color. 
When I open the help screen and select 'Printing,Faxing, and Scaning' I get the message below:
	
The requested page is not found in the document /usr/share/gnome/help/printing/c/printing.xml

when I 'CD' to the directory indicated and double click on the document, Mozilla firefox reports the message below:

XML Parsing Error: undefined entity
Location: file:///usr/share/gnome/help/printing/C/printing.xml
Line Number 18, Column 6:    	
	&legalnotice;
--------^

When I do a 'search for files" using 'printing.xml' there is a whole bunch of ../printing/.. directories, Im assuming they are associated with different languages. So I went into the en_GB directory and double clicked on that file and got the message below:
        
	This XML file does not appear to have any style information associated with it. The document tree is shown below.
-
	<article id="print-fax-scan" status="writing" lang="en_GB">
-
	<articleinfo>
<title>Printing, Faxing and Scanning</title>
-

ETC..ETC..ETC............
 I don't know anything about XML so I don't know what the problem is.
 I noticed that other help files could not be found, so I guess I have other problems.
Does anyone else have similar help problems?
Can anyone tell me whats going on?

---

### Post by Xiong Chiamiov on 2008-03-17
XML is very similar to html, except in that you use whatever tags you wish (simplified).  I'm not very comfortable with xml, but it appears to me that whoever wrote the file made some sort of error, which is why you get the parsing error.

---

### Post by marioub on 2008-03-17
Xiong Chiamiov: Thank you for your reply.

You may be correct, but this problem appears in quite a few places when I try to invoke help for specific subjects.
It's a new install and I'm a NEWBEE to ubuntu.

I'm wondering if I did a faulty install or have corrupted files on my install disk (UBUNTU 7.10).

I don't want to start over and get the same results.

Since these help files are part of the install and I want to use help with certain setups of hardware, I find these file critical to my MENTAL health and for the successful setup of my system!

Can  anyone offer me a solution?

Any help will be appreciated!

---

### Post by frisket on 2008-03-20
> **marioub said:**
> My multifunction Epson Stylus CX4800 seems to install just fine and printing works fine, but when I try to scan, I just get black and white with no color. 
When I open the help screen and select 'Printing,Faxing, and Scaning' I get the message below:
	
The requested page is not found in the document /usr/share/gnome/help/printing/c/printing.xml

when I 'CD' to the directory indicated and double click on the document, Mozilla firefox reports the message below:

XML Parsing Error: undefined entity
Location: file:///usr/share/gnome/help/printing/C/printing.xml
Line Number 18, Column 6:    	
	&legalnotice;
--------^


Browsers don't support all of XML. In fact browser support for XML is so broken
I never serve XML...I use Cocoon to generate HTML on the fly and serve that.

P

---

### Post by marioub on 2008-03-22
Thank you frisket!
Your response is greatly appreciated!
I just can't seem to get it in my head that there is no way that I'm going to be able to use 'HELP' on my Ubuntu installation.

Thanks again.

---

