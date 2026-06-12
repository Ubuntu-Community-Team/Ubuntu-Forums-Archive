---
title: "CUPS (command line and other questions)."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-04-21
Ok so I have installed my printer using cups ([http://localhost:631)](http://localhost:631)). And it works well.

However I have a few other computers on that lan to setup to use that printer also.

So I thought it would be better if there was away to setup cups via the command line. Then all I would then have to do write a script. Then run the script on all my machines. This sound much nicer then having to goto each machine and doing the long process.

Stats on my printer:
Description: HP Deskjet 840C
Location: Server
Make and Model: HP DeskJet 840C Foomatic/hpijs (recommended)
Printer State: idle, accepting jobs, published.
Device URI: lpd://10.1.1.217/lp1

Also just if the stats did not make sense to anyone, I purchased a serial to print server adapter. So I have turned my HP Deskjet 840C into a print server that is connected straight into the lan. This is awesome because I do not need to make sure that a certain computer is on to use my printer.

Anyways how would I go about doing this?


Also another problem I am having is that my partners lecturer at the university makes his note available via power point presentation. This is ok because we have OpenOffice. However he makes the background back, and the foreground white. My poor black ink cartage. I can not find away to invert the colors on print, so we have to go thought each slide and edit them. This is stupid. So I thought maybe if there was a way to edit the driver you could find the instructions for the colors and swap them over (inverting them).  Then setup the printer again but with the second driver. So you would have to printers to choose however one would print inverted colors.

Any ideas?

---

### Post by UltraMathMan on 2007-04-21
Check out the CUPS SAM for info on [Adding Printers from the Command Line]("http://cups.org/doc-1.1/sam.html#4_2_1")

-Hope this helps :)

---

