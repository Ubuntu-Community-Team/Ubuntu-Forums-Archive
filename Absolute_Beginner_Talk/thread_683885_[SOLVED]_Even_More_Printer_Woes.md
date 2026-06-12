---
title: "[SOLVED] Even More Printer Woes"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-01-31
Could someone please help me? 
I have read and reread this forum on printer problems with no obvious answer.
When I installed UB a few weeks back the printer (HP 7760) worked, not just a test page. Could someone please list me some checks to find out what is wrong.
I am not fussed about printing photos, just simple text.

---

### Post by cmnorton on 2008-01-31
Does the printer show up in System --> Administration --> Printing ?

Can you queue a print job to the printer?

If you can check various logs in /var/log/cups to see if there is anything there, especially error_log.

What about unconfiguring and then reconfiguring the printer?

Try unconfiguring and reconfiguring it. What happens?

---

### Post by LowSky on 2008-01-31
it may be a odd HP printer glitch.... did you turn off the printer anytime lately? Thats would do it

goggle HPLIP and install it and follow the instructions.. it willl fix everything

---

### Post by newbeeman on 2008-01-31
> **cmnorton said:**
> Does the printer show up in System --> Administration --> Printing ?

Can you queue a print job to the printer?
If you can check various logs in /var/log/cups to see if there is anything there, especially error_log.
What about unconfiguring and then reconfiguring the printer?
Try unconfiguring and reconfiguring it. What happens?


Found it. On checking the printer set up I noticed the URI was pointing to the wrong setting. 

Changed that and it works. 

Sorry to trouble you.

---

