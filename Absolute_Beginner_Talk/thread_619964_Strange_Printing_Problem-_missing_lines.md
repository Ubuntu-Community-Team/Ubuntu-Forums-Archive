---
title: "Strange Printing Problem- missing lines"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-22
I've just plugged in my printer for the first time since installing Ubuntu (7.10).
Ubuntu detected the printer immediately which was great, but when I print for example a page of text, it doesn't seem to be printing the whole page- it misses out a couple of lines at a time, then prints for a few lines, then misses out some lines etc.

Printer has worked fine for a few years on Windows up till now, so I doubt VERY much that the printer's faulty.

Seems to me as though it's not operating properly due to new operating system.

It is a HP Deskjet 5740.

I looked in Ubuntu and Linux databases and there seems to be no issues with this printer- 'works perfectly' apparently.

I looked in printer configuration options but couldn't see anything which might help.

Any suggestions?

---

### Post by 01steven on 2007-11-25
any thoughts on this please?

---

### Post by 01steven on 2007-11-27
I assume no-one can help?

---

### Post by alienexplorers on 2007-11-27
Are you running the correct driver.
> Model Name 	Min. HPLIP Version 	Parallel 	USB 	Network 	Print Class 	Scan 	Photo 	Fax 	Copy 	Services/Status
Deskjet 5740	   0.9.5 	No	  Yes	  No	  DJGenericVIP 	  No	  No	  No	  No 	  Yes
Is your printer set for bi-directional or uni-directional printing.

---

### Post by 01steven on 2007-11-27
Please can you tell me how to check this?
Thanks

---

### Post by 01steven on 2007-11-29
If anyone can tell me how to check this I'd appreciate it.
Regards

---

### Post by 11hjpphty76lkjj on 2007-11-29
Can you check in the BIOS? What's your parallel port set to?

A

---

### Post by 01steven on 2007-12-03
Sorry please can you explain how to do this?
Thanks

---

### Post by 11hjpphty76lkjj on 2007-12-03
I can't--it depends on your computer.  Your computer documentation should tell you how to get into the BIOS and to where check the setting.  Sorry I can't help with that. :(

Usually after you reboot the computer you press say F1 or some other combination of keys when prompted. It might say [To enter setup press F12] just after you reboot the computer.

Not much help but it hope it points you in the right direction.

A

---

### Post by snippl on 2007-12-06
Ubuntu 7.10 / HP Deskjet 845c

i think i might have the same problem.


what the problem looks like:

-print any document (textfile, pdf, website or ubuntu-/cups- testpage)
-printed sheet is striped horizontally: 
comparing lines that are next to each other (above or under) one can see that the intensity of the ink changes. 
however the intensity does not change within a line itself and there is no indication that the catrige head itself is dirty since it is brand new ;) .


what i did to approach the problem:

-changed between the printout modes and testpaged them.
-opened cups via my browser on localhost:631 , a hp-printer and a  pdf-printer are signed. thats cool with me.
-tried to change the driver. 
since i dont know much about it i simply changed it via "system > administration > printing". 
hpijs, foomatic or gutenprint didnt solve the problem, every test page had the same result.


what i think the problem might be:

-the printer is broken, gotta check if its working under ms-windows %) .


mini tiny help or neat solutions are both much appreciated!

---

### Post by stchman on 2007-12-06
> **01steven said:**
> I've just plugged in my printer for the first time since installing Ubuntu (7.10).
Ubuntu detected the printer immediately which was great, but when I print for example a page of text, it doesn't seem to be printing the whole page- it misses out a couple of lines at a time, then prints for a few lines, then misses out some lines etc.

Printer has worked fine for a few years on Windows up till now, so I doubt VERY much that the printer's faulty.

Seems to me as though it's not operating properly due to new operating system.

It is a HP Deskjet 5740.

I looked in Ubuntu and Linux databases and there seems to be no issues with this printer- 'works perfectly' apparently.

I looked in printer configuration options but couldn't see anything which might help.

Any suggestions?

Yes, I checked and and the works perfectly applies.

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_5740](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_5740)

Make sure the hpijs driver is selected.

---

