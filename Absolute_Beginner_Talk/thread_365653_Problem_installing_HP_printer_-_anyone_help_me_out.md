---
title: "Problem installing HP printer - anyone help me out please ??"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-02-19
I am trying to install an HP C5140 Photosmart printer on my Ubuntu Dapper system, and am being asked for the network printer URI. Being a noob to the nth power, I have no idea what that is. Anyone tell me how to find this so I can finish installing the printer ?  Thank you for your help now and in the past, this has been a fun and enlightening experience for this (almost done with Gates) windoz user. Thanks again.

---

### Post by NewOldTimer on 2007-02-19
see here>>>     [http://ubuntuforums.org/showthread.php?t=362234](http://ubuntuforums.org/showthread.php?t=362234)

---

### Post by ramjet_1953 on 2007-02-20
> **jerrynewt said:**
> I am trying to install an HP C5140 Photosmart printer on my Ubuntu Dapper system, and am being asked for the network printer URI. Being a noob to the nth power, I have no idea what that is. Anyone tell me how to find this so I can finish installing the printer ?  Thank you for your help now and in the past, this has been a fun and enlightening experience for this (almost done with Gates) windoz user. Thanks again.

Is your computer on a network, or stand alone?

If it is stand alone you should be installing your printer as a local printer.

Regards,
Roger :cool:

---

### Post by jerrynewt on 2007-02-20
I have it networked vie ethernet cable hooked up to my router, as well as the other 3 comps. 1 XP, 1 dual boot ubuntu and XP, and one ubuntu only. The printer has an ethernet plug and I went from it to the router. (Belkin) All comps can ping each other and all have internet connection as well.

---

### Post by Maestro23 on 2007-02-20
> **jerrynewt said:**
> I have it networked vie ethernet cable hooked up to my router, as well as the other 3 comps. 1 XP, 1 dual boot ubuntu and XP, and one ubuntu only. The printer has an ethernet plug and I went from it to the router. (Belkin) All comps can ping each other and all have internet connection as well.

It should have an IP address then... correct?

---

### Post by philip360 on 2007-02-20
Hi, I had difficulty getting my printer to work and here is how I solved the problem:
My box, hooked to D-link DSL-604+ router and HP Deskjet 6840 also pluged into the router

System--Administration--Printing:
Select "Install new printer"
Select "Network Printer"
Select "HP JetDirect"

Next step:
Host: Type in the IP Address for the printer which I got from the "print report" function on the printer.
Port: 9100 (this was already filled in)

Select Printer model
The driver is automatically selected by checking your printer model
I did not have to install any driver steps

Description: the printer
Location: on my desk

Then I was happy and it worked. There was an option to print a test page and it worked.

Hope this helps, it was the result of much trial and error with CUPS and all that stuff
Philip.

---

### Post by Carl Wachsman on 2007-03-01
This is correct.

System--Administration--Printing:
Select "Install new printer"
Select "Network Printer"
Select "HP JetDirect"

Next step:
Host: Type in the IP Address for the printer which I got from the "print report" function on the printer.

In  the Jetdirect printed report there is a HOST NAME ie: (NPI1AC579).  This is NOT to be entered. The IP ADDRESS must be entered on that line. This has not been clear in any of the posts. Good Luck
Carl

---

