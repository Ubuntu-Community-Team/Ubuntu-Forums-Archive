---
title: "Printer Is Recognized but Won't Function"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by pjmaggitti on 2007-02-13
How can I get my Canon Pixma iP1500 to work? There is no driver for that specific model available via Ubuntu, so I chose the one that was recommended by Ubuntu. When I attempted to print, I saw a printer icon appear, but nothing happened. I checked a database and learned that this printer model worked "mostly." Am I going to have to buy a Ubuntu-friendly printer. If so, any suggestions?

Thank you.

Phil Maggitti

---

### Post by lhtown on 2007-02-13
I would suggest checking to make sure you are using the gutenprint driver that they recommend.

---

### Post by pjmaggitti on 2007-02-13
How do I do that? I clicked the install-driver button at one point in my stumbling around, but I beat a hasty retreat when I got a pop-up screen that asked me to select a PDF file. Did I need to continue installing at that point, or is the installation automatic? If I should have continued, what PDF file should I have chosen?

Thanks.

Phil Maggitti

---

### Post by lhtown on 2007-02-13
Go to System>Administration>Printing. In the box that opens, there should be an icon that says "new printer" and another icon representing your printer. Right click on the icon that represents your printer (it should be named something that refers to your printer like iP1500) and select properties. In the dialog box that opens, click on the tab labeled "driver". The manufacturer should read 'Canon', the model number should probably be 'iP4000' (since that appears to be the printer that would be the closest to yours and it installs the correct driver),  that should automatically change the driver to "gutenprint". You DON'T need to click on "install driver". The driver is already installed on your system by default. Just click close.

If that doesn't work for you, post back and let us know what you have. Also, you might want to play with some of the other options on the other tabs in that box like paper size and so forth.

---

