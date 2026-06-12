---
title: "Printer Cover Sheet"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by KevL on 2007-03-19
My first post here, linux newbie.
I'm not sure where this problem lies so I will start here.

I have a HP multifunction printer connected to my computer running Edgy. The printer uses the hplip drivers and everything seemed fine. The problem arose when I printed a web page. I got a "Confidential " cover sheet/ jobsheet.
This only happens when printing from Firefox. I have checked the etc/cups/printers.conf and the jobsheet line is set at none none.
The printer is used by 2 winxp computers on my network and neither of them print a jobsheet. 
Any assistance saving a lot of paper would be greatly appreciated

Kev

---

### Post by Patrick K on 2007-03-19
You might type "about:config" in firefox's url window. Maybe you'll see something there. Type "print" in the filter window. This will bring up all the settings with print in them. I looked in my setup but didn't see anything. Your's might be different.

---

### Post by KevL on 2007-03-19
I've checked about:config and cannot find anything relevant.
 The cover sheet that is printing is a CUPS coversheet, says Confidential top and bottom, job title in the middle C Unix printing system in bottom left and Easy Software Products bottom right. Somewhere in the CUPS setup is another config file that must be telling it this but only for Firefox that I've noticed so far.

Edit
This also occurs in opera. There must be a browser printing conf file somewhere .


Kev

---

