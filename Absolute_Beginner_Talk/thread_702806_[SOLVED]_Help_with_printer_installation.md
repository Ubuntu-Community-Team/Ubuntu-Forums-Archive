---
title: "[SOLVED] Help with printer installation"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-02-20
I currently have Ubuntu and windows, only reason I have windows is due to my printer. So if I could get this darn printer working in Ubuntu I am going to make the full switch. It is a 'Brother HL-1440' printer. It came with an installation disc, but says for windows and Mac only. I have seen some people got this printer working, but they didn't explain how. If anyone knows how to that would help me a lot.

---

### Post by Moop on 2008-02-20
Your printer is listed in the driver section. Have you tried adding it as a new printer and then choosing the driver from the list?

System-Administration-Printing

---

### Post by steve-shinn on 2008-02-20
That printer should work out of the box ! :-
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother)

---

### Post by ImThatNerd on 2008-02-20
> **steve-shinn said:**
> That printer should work out of the box ! :-
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother)

Ah darn, I should have searched a little longer. I am curious what to select when adding a printer...

[IMG]http://i26.tinypic.com/b6r60k.png[/IMG]

---

### Post by Moop on 2008-02-20
If it's hooked to your computer choose LPT#1. If it's on a different windows PC choose the samba option.

---

### Post by ImThatNerd on 2008-02-20
I will try LPT#1, it is on this computer. I already uninstalled windows and reformatted and reinstalled Ubuntu since I just got it the other day and installed nothing yet.

---

### Post by markharding557 on 2008-02-20
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")
you need to get debian drivers from the above site and install these on my set up i had to install an lpr driver followed by a cupswrapper driver it may be different for yours depending on the model

---

### Post by ImThatNerd on 2008-02-20
> **markharding557 said:**
> [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")
you need to get debian drivers from the above site and install these on my set up i had to install an lpr driver followed by a cupswrapper driver it may be different for yours depending on the model

I followed the posts above and got it working perfect! The LPT#1 worked fine, printed a test page and it is beautiful. Thank you so much everyone on the help in this thread. markharding I will thank you as well since that would probably have worked if what I did, didn't. 

Ha now I can make the full switch to Ubuntu, yay.

---

