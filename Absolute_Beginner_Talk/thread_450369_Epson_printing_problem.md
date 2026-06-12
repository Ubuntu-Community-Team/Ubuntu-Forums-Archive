---
title: "Epson printing problem"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by bob74 on 2007-05-21
Can anyone out there please help me to get my Epson Stylus Color 740 working.
Please don't refer me to a web site- I've tried them all and got no where. Some
concise instructions devoid of geek talk would be very much appreciated. (Feisty
by the way)

---

### Post by adwatkin19 on 2007-05-21
Hi there

[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

try that website, i think they have the drivers you need, if not google "ubuntu + print make and model"

hope that helps 

adwatkin19

---

### Post by BAS54 on 2007-05-21
Hi bob74

I just installed an Epson Stylus Colour460.
If I can help.
Geek talk. Boy am I fed up with that.
Exactly what is wrong?
I found Dapper Drake chock full of Epson drivers.


BAS54

---

### Post by bob74 on 2007-05-21
Hello
Thanks for your quick responses- Can you explain where I am going wrong.
I click sys/admin/printing and get to page 1 of printer setup which says no printer detected.
I have checked on my other dual boot system(Me) and on that the printer functions OK so everything is connected. If I look at " use another printer by specifying another port" I find Parallel
port No1  is Canon(my scanner) and Epson. I leave at lpt 1 to step 2 and select Epson 740 etc
Click on 740 and install driver. Another page appears with "select a ppd file" but there are none shewn, where ever I look.
On the face of it there should be a printer driver on the system.
I went to the website to obtain the driver but it appears not to be  a ppd file so I am stuck.
Any other help?

---

### Post by guitarchris on 2007-05-21
No geek talk from me either - I don't know any;) But I am trying to install my Stylus DX3850 in Ubuntustudio (Feisty) at this very moment.
To find the installed drivers (took me a while) click on the drop down arrow in the box to the left of "Install driver". I was presented with two - expert and simple.
Mine still doesn't work tho:( I think I have to enter something in the "Location " box but I don't know what. I tried entering "USB" to no avail. 
I'ld better go and have alook for the answer........

9 mins later - mine works now I've selected local instead of network printer. Silly me.

---

### Post by Bakerman on 2007-05-21
Hi, I have an Epson Stylus Colour 460. I use the 'High Quality Image (Gutenprint) (en)' driver from the driver drop down list. I've never had to install a PPD file to get it to print. I seem to remember reading somewhere that this driver is a modified Gimp print driver. It works perfectly. The 740 is also listed in the Epson section, on Edgy it is anyway. I don't have access to a feisty box, so someone else will have to let you know if it's available on your version.

Also, there's a app in Synaptic called Mtink that is quite useful for checking ink levels & head cleaning etc.

---

### Post by bob74 on 2007-05-21
Thanks again to those who responded I am now sorted. If I had the first time scrolled down further
on the linux.org page I would  I would have seen the pdd file. Once downloaded I could access it from the desktop and bingo  everything worked a treat. Hip, hip hooray I am almost at the final stage at getting all necessary apps installed.
Thanks again from an elderly  Ubuntu fan.

---

### Post by Howlin' Hobbit on 2008-02-01
> **Bakerman said:**
> Hi, I have an Epson Stylus Colour 460. I use the 'High Quality Image (Gutenprint) (en)' driver from the driver drop down list.

I have the 740i and it was giving me all sorts of grief until I read your message about the Gutenprint driver. Works like a champ now. Thanks!

---

