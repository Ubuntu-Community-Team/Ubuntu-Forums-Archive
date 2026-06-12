---
title: "[SOLVED] Epson Stylus DX6000"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by giles.wheatley on 2007-07-20
Hi - I have a problem with setting up printing. I have installed Feisty and have it successfully running on a Windows network. Using the New Printer facility I can find the Epson Stylus DX6000 that is connected and shared on an XP box on my network. However, the DX6000 is not listed by the New Printer facility. I have looked at the various forums on the web and although having tried various things but keep hitting brick walls. Please can anyone help?

Many thanks
Giles

---

### Post by nrpgeek on 2007-07-21
Hi, I'm no expert (fortnight experience of Linux!) but I had a very similar problem for a few days until I stumbled across the answer. Try this, it worked for me...
1) Open the printers window as before.

2) Before you add a new printer, select "Global Settings” from the menu bar and then “Detect LAN Printers". This is turned off by default as it is a security 'hole'. Wait a minute or two for it to scan the network.

3) Go through the same routine - select windows network, then choose which pc, then the printer using the list boxes - you may need to supply a username & password.

4) Finally choosethe correct driver (you may have to search the documentation for more help on that - I've only installed HP printers so far) - that may be as simple as choosing it from the list. Then "Install"

5) !!IMPORTANT!! Remember to turn off the "Detect Lan Computers" when finished to restore your security settings.

All of the above assumes that the shared printer PC is turned on, has the necessary permissions turned on, etc, etc, - if you're a Window$ user, you'll know all that --- if so sorry.

Let me know how you go on...

---

### Post by giles.wheatley on 2007-08-10
Hi,

Thanks but the problem is that the DX6000 is not listed in the printer install utility.
Anyone know how I get get hold of the correct drivers?

Giles

---

### Post by Mzee nyuki mpya on 2007-08-10
I had a problem with installing an Epson (different model, not on a network). Eventually I found that the way to install was through CUPS (Common Unix Printing System). 
However, CUPS isn't listed in Applications or System! To use CUPS, open your browser and type the following into the address window:

[http://localhost:631/](http://localhost:631/)

CUPS opens and it is a nice easy GUI way to install your printer with all the instructions you need.

---

### Post by yorkie on 2007-08-10
go to
 [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
It will show you how to find and install your printer I followed the instruction to make sure there is a driver for your printer and there is
good luck

---

### Post by giles.wheatley on 2007-08-13
Many thanks to all - I have manged to resolve this using CUPS.
Giles

---

### Post by schorsch on 2007-08-13
Could you please then mark  the thread as solved? Others will then know that there is answer inside ... :-)

---

### Post by giles.wheatley on 2007-08-20
Sorry - how do I do that?

---

### Post by schorsch on 2007-08-20
In the top right there is a link called "Thread Tools". There you can mark the thread as solved.

---

### Post by Diggla on 2007-08-20
Hi 

I know this query has been solved, i actually used some of the info provided to solve the problem I had, however I may have found an easier solution.

All I did was go through the add printer setup and used the Epson DX4800 driver and it works on my DX6050. Printed out test page fine.

I am using Ubuntu Feisty on my laptop and using the printer via my Windows PC.

Regards

Diggla

---

