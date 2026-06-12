---
title: "Printer Configuration Problem"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by tstrickland on 2005-06-22
Just installed Ubuntu - setup went perfectly. Couldn't have been better :-)  It recognized my printer (Canon S300) and it prints fine. One problem - it only prints on the left 5 inches of the page, leaving 3.5 inches blank on the right. I've selected US Letter for the document size but that doesn't seem to matter. What to do? :-? 

BTW, I'm a newbie, and before installing Ubantu I spent about 10 days trying to install Mandriva. Reinstalled 4 or 5 times, etc. Nothing worked. Went to Ubuntu and everything works great. I'm afraid to change much of anything! :grin:

---

### Post by az on 2005-06-22
Is this consistent among any application from which you print?  Like are you only printing something from firefox?  Or it happends regardless of the application.  Is anything cut off or is it just shrunk?

---

### Post by tstrickland on 2005-06-22
[QUOTE=azz]Is this consistent among any application from which you print?  Like are you only printing something from firefox?  Or it happends regardless of the application.  Is anything cut off or is it just shrunk?[/QUOTE]
 It is not consistnet among applications. I just printed it in Open Office and it printed the whole page in a 1.5x3 inch area in the upper left hand of the page. Previously I had printed with gedit. A4 seems to be the default page size but I change it to US Letter. Don't know how to make US Letter the default for all applications.

BTW, nothing is cut off. It prints the whole page but in a small area of the page.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=tstrickland]It is not consistnet among applications. I just printed it in Open Office and it printed the whole page in a 1.5x3 inch area in the upper left hand of the page. Previously I had printed with gedit. A4 seems to be the default page size but I change it to US Letter. Don't know how to make US Letter the default for all applications.

BTW, nothing is cut off. It prints the whole page but in a small area of the page.[/QUOTE]


Can you install abiword and tell me what it does?:

> sudo apt-get install abiword

---

### Post by tstrickland on 2005-06-22
[QUOTE=poofyhairguy]Can you install abiword and tell me what it does?:[/QUOTE]
 It couldn't find abiword but it suggested abiword-gnome. Assume it's the same. Installed it and set up page size as letter size. It printed the document in the upper quarter of the page - a section ~4 inches wide and ~ 5.5 inches tall. The print preview shows the document occupying the entire page.

---

### Post by tstrickland on 2005-06-23
After much searching and frustration, I found a reference that recommended using the Canon BJC 8200 driver. I checked and there's a BJC 8200 and a BJC-8200 driver. Both worked but the BJC-8200 produced the better quality of print. 

Thanks for your help!

---

### Post by jcrochford on 2006-11-03
tstrickland,

I think you've figured this problem out.  I have a Canon S900 printer.  I've tried the S800 drivers and the Ubuntu-recommended (i.e., detected) bjc-600 drivers.  In each case, I had problems with my printed pages appearing on only the upper-left third of the page.  I switched to the BJC-8200 and now life is better.  Thanks for the info!

Later,
jcrochford

---

