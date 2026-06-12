---
title: "[SOLVED] Epson Stylus 600 not printing"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by tahitiwibble on 2007-08-15
Please help if anyone can. :confused:

I try to print the test page and the whole process goes on but all windows close and nothing is printed?

The driver is the best one for the job, the cable is ok ........ what to do?

---

### Post by tahitiwibble on 2007-08-15
Ladies, Gentlemen, Boys or Girls **PLEASE** ............. I am **desperate** here. 

and **THANKS** in advance

[-o<

---

### Post by ramjet_1953 on 2007-08-15
This link may be of help:

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_600](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_600)

This should work OK.

Failing that TurboPrint claim that their driver works with your printer. TurboPrint is not free, but you can download an evaluation version to test before paying.

[http://www.turboprint.de/english.htm](http://www.turboprint.de/english.htm)

Regards,
Roger :cool:

---

### Post by tahitiwibble on 2007-08-17
Roger, are you still there?

I still have no joy.

I tried everything that I know how to do and every suggestion that I found on more than one forum. I installed TurboPrint. I checked the cable and printer on another computer and it works perfectly well.

Always the same result, the whole "print test page" procedure fully terminates as though everything went OK but the printer doesn't even make a squeek.

Is there a way to check the printer port itself perhaps?

---

### Post by ramjet_1953 on 2007-08-19
Is this printer plugged into a USB, or Parallel printer port?

I'm not very familiar with Epson printers, so I don't know what interfaces this model has.

If it is plugged into a USB port, you could try changing the port it is plugged into.

Also, I assume that this printer is actually OK? Have you tried it on another system / OS?

Also most printers have an inbuilt self-test mode, where you hold down one or two of the buttons on the printer while powering it up.

Have a look in your printer manual to see how it's done and carry out a self test, to make sure that it passes.

Let me know how you go.

Regards,
Roger :cool:

---

### Post by tahitiwibble on 2007-08-19
I have successfully tested the printer with a friends XP Pro powered laptop and everything is just Jim Dandy; test pages print beautifully, both from the self-test mode and when I send info from the computer! Printer and cable work perfectly therefore.

The printer is on the LPT1 parallel port and does not have USB capability. Although I did check USB printing with one of my daughters USB printers and it also functions perfectly well.

Is there some way in Feisty to check the path that the print info is taking? 

Is it perhaps the parallel port which is broken? Is this detectable and how? The print info just isn't making it to the parallel port for some reason.

---

### Post by tahitiwibble on 2007-08-25
Turned out to be a dead parallel port.

The solution was to buy a cheap usb-parallel adapter cable and Bob's your Uncle. The cable worked beautifully without need to manually install drivers or anything.

---

