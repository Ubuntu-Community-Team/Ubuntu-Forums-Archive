---
title: "Epson R265"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by PhatPhil on 2007-12-29
I have installed kubuntu 7.10 about a week ago therefore a newby after 13 years of various versions of windows.

I have studied ubuntu posts and variuos articles found on Google for my problem.

My problem is creating a PPD file for my Epson R265 printer
What I have done so far.

Downloaded 
pipslite-cups_1.0.1-1_i386.rpm

used following commands
sudo alien -i pipslite-cups_1.0.1-1_i386.rpm --script
sudo /usr/share/pipslite/setup
sudo /usr/bin/pipslite-install

All appears to work well until I try and create the PPD file - the Continue button is disabled.

Any help would be apprecited

---

### Post by markharding557 on 2007-12-30
found a link to a deb installer file for your printer 
[http://www.da-cha.jp/?q=node/296]("http://www.da-cha.jp/?q=node/296")
also i noticed you used alien to convert rpm to script,some of the posts i have seen indicate that rpm should be converted to deb

---

### Post by PhatPhil on 2007-12-30
Thanks for the advice.

I created the Deb file first and installed it but I am still having the same problem creating the PPD file.

:confused:

---

### Post by philinux on 2007-12-30
R265 is supported in gutsy whats the advantage of the ppd driver.

i have an R200 so I'm interested.

---

### Post by PhatPhil on 2007-12-30
I am surprised you say that the Epson R265 is supported.

If I go through System Settings and Add Printer and go through the Epson printers the R265 is not listed or I am I missing something.

---

### Post by philinux on 2007-12-31
Ah I assumed kubuntu would be the same as ubuntu. Your printer shows up when I try add printer on my system. Odd. 

Mine is a standard gutsy clean install.

---

### Post by cotcot on 2007-12-31
1. I installed pipslite the same way as you did and found the eklite.ppd in the /usr/share/cups/model/ folder. I installed a new printer in cups and pointed to this driver. Printer is working. (photo stylus RX640). So if you get from avasys-epson the same driver as suggestion for your printer it should work this way.

2.  If your printer is Epson Stylus Photo R265 than if have seen your driver in gutenprint.
Install it with cups (browse to [http://localhost:631/](http://localhost:631/) and install the printer).

---

### Post by PhatPhil on 2007-12-31
Thanks Cotcot

Just the piece of information I was missing.

For any others following this thread,

Go to add printer and instead of looking in the model list go to other and point to the eklite.ppd file.

I can now print the test page.

:KS:KS:KS

---

### Post by cotcot on 2007-12-31
It is 'only' pipslite. For most print jobs it is convenient.
If you need other paper sizes you will need the gutenprint. You can define in cups a second printer with the gutenprint driver. That is a full size one. Whenever you need to print something you will have the choice. 
In my case the gutenprint driver works except for the color and density that i had to adjust.

Can you, as a courtesy to others,  mark the thread as solved ? (click edit on your first post and then click on the 'advanced' button , that will allow you to change the title; you could put [SOLVED]).

---

