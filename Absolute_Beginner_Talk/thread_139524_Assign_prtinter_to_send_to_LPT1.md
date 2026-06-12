---
title: "Assign prtinter to send to LPT1"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-03-04
How do I assign my printer to send to LPT1 with 5.10 BBadger?

---

### Post by 5-HT on 2006-03-04
Hi, do you want to configure the printer to use LPT (parallel port) or is this something about line printer configuration? 

If it's about the the LPT port and you haven't configured it yet:
 simply go to System > Administration > Pinting and walk through the wizard to set it up. Detected printers (local and network) will be shown along with which port they are using (for local), so have it plugged in to LPT if that is what you want.

If it's about the LPT port and you have already configured it:
 go again to 'Printing', right click on your printer, select properties, click on the connection tab, and you should be able to change it from there.

I've noticed that it was necessary at times to have to shutdown the computer, connect the printer in the manner I wanted, then restart for the wizard to detect the changes (say, in changing from USB to parallel).

Hope this helps

---

