---
title: "Epson Stylus CXxxxx printers"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by doctor bangali on 2007-05-08
I noticed something distressing, I just upgraded the Kubuntu on my desktop to Feisty and I noticed that the list of Epson Stylus printers in the KDE print wizard did not include any name of the form CXxxxx, I had noticed something like CX6500 in Dapper, but no such names here.

What happened?

---

### Post by tophatandy on 2007-05-08
Is your printer not working, or did you just notice it?

---

### Post by doctor bangali on 2007-05-08
My printer is working ( on Windows). On Dapper I used the KDE print wizard, I didn't find an exact match for my printer (CX6000), I tried using CX8xxx driver (which I had heard should work for this printer), but it printed a ton of blank sheets.

It was then I upgraded to Feisty on my Desktop, hoping it would support more printers.

---

### Post by Tanker Bob on 2007-05-08
These newer printers don't appear in the wizard for some reason, but the driver is in CUPS.  You need to go to your local CUPS server at [http://localhost:631/](http://localhost:631/) via your browser, click on the Manage Printers tab, and add it from there.  The process is straightforward, very similar to the wizard.  Printer works fine once you add it in CUPS.

---

### Post by doctor bangali on 2007-05-08
Tthe Ubuntu live CD detects my Printer on my Desktop.

---

### Post by doctor bangali on 2007-05-08
but Kubuntu lived CD does not!

---

### Post by doctor bangali on 2007-05-08
> **Tanker Bob said:**
> These newer printers don't appear in the wizard for some reason, but the driver is in CUPS.  You need to go to your local CUPS server at [http://localhost:631/](http://localhost:631/) via your browser, click on the Manage Printers tab, and add it from there.  The process is straightforward, very similar to the wizard.  Printer works fine once you add it in CUPS.

When I click on manage printers I am told to "Search in printers". What do I do next. I tried searching for Stylus CX6000 etc.

---

### Post by Tanker Bob on 2007-05-08
I don't have my Kubuntu system in front of me right now.   I believe that there's an Add Printer selection available on the Manage Printers page.  There's a nice description of the process [here](http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_1_3).

---

### Post by doctor bangali on 2007-05-08
> **Tanker Bob said:**
> I don't have my Kubuntu system in front of me right now.   I believe that there's an Add Printer selection available on the Manage Printers page.  There's a nice description of the process [here](http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_1_3).

I have the printer test page in my hand. It worked like a charm. Thanks!

---

### Post by Tanker Bob on 2007-05-08
Glad it worked out for you!  I have a CX7800 that I really like.

---

### Post by doctor bangali on 2007-05-12
Tanker Bob,
Any ideas on how to get the scanner working. xsane does not detect it.

---

### Post by Tanker Bob on 2007-05-12
> **doctor bangali said:**
> Tanker Bob,
Any ideas on how to get the scanner working. xsane does not detect it.
No, and Feisty in its current kernel release will not recognize it.  The kernel team introduced a USB suspend feature for laptops in Feisty that breaks support for all scanners.  Older scanners have a workaround with something called Scanbuttond in the repositories, but it won't work with newer scanners.  You can read the whole sad story [here](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488).  According to that thread, the Linux kernel team just fixed the problem, but the ubuntu team hasn't updated our kernel with the fix yet.  I remains to be seen if they ever will.  All of which means that I have to fix my WinXP dual-boot setup today.

---

### Post by doctor bangali on 2007-05-12
That smells bad.
I will be very careful before saying things like "linux is ready for the desktop" in future.

---

### Post by strabes on 2007-05-12
Tanker Bob: Thank you so much!!! Adding it manually through localhost:631 worked perfectly!!!! I have such a feeling of victory right now - I am smarter than my printer ha ha!

---

### Post by Lopar-XL on 2007-06-01
Thank you.  This tip has been helpful.  I have Ubuntu Feisty Fawn v7.04 and an Epson Stylus CX6000 all-in-one, and I'd like to enable double sided printing.  Does anybody know how to do that?  The Double Sided option in the Paper tab is not functioning.

---

