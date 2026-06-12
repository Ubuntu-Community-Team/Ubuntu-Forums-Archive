---
title: "Network Printer, Can't Print"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by mssinstructor on 2006-11-29
I am an absolute beginner. I have a Ubuntu 5.10 ini a small LAN connected to another LAN. My HP Laserjet 4000 printer is using IP is 10.10.7.253 on the second LAN.

I can ping the printer fine, but I cannot print a test page. I've downloaded and installed the HPLIP driver, but it didn't help. I've tried the web interface with localhost, but I don't have a password to access it.

Please help. What do I need to do?

---

### Post by crispy_420 on 2006-11-29
What do you mean "another LAN"? 

What kind of comp is it hooked into? (windows, linux, etc.)

---

### Post by taurus on 2006-11-29
We have a few network HP LaserJet 4200s and I can send my stuff to them just fine.  

System -> Administration -> Printing -> New Printer -> Network Printer and pick Unix Printer (LPD).  Now, enter the IP address of your printer in the Host: and enter lpd in the Queue:.  Click Forward to move to the next screen and pick out the model for your HP.  You don't have to install any extra driver since it comes with a driver for your HP printer...

---

### Post by mssinstructor on 2006-11-29
Taurus, you are right on. Thanks.

---

### Post by taurus on 2006-11-29
So you can print to your network HP printer now.  Glad to hear it works for you too.

---

### Post by pacificdrums on 2006-11-29
> **taurus said:**
> We have a few network HP LaserJet 4200s and I can send my stuff to them just fine.  

System -> Administration -> Printing -> New Printer -> Network Printer and pick Unix Printer (LPD).  Now, enter the IP address of your printer in the Host: and enter lpd in the Queue:.  Click Forward to move to the next screen and pick out the model for your HP.  You don't have to install any extra driver since it comes with a driver for your HP printer...

Thank you so much!! This worked great with my Xerox Docuprint n17. Figures, it did not work because I added it wrong :rolleyes:. Thanks again :-D

---

