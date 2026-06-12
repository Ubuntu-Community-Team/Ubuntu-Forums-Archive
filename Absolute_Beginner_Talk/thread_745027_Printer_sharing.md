---
title: "Printer sharing"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-04-04
Hi All

We have two PC's running One with Gutsy and my daughters with PCLinuxOS ,both connected to a Speedtouch Modem/router. There is a printer connected to the Ubuntu box .Can some one please advise me on how to set it up so my daughter can use the printer via her PCLinuxOS box ? There seem to be plenty of guides for printer sharing with windows but I haven't come across one for this combination of distros.
Thanks 
Steve

---

### Post by brian_p on 2008-04-04
> **bossa said:**
> Hi All

We have two PC's running One with Gutsy and my daughters with PCLinuxOS ,both connected to a Speedtouch Modem/router. There is a printer connected to the Ubuntu box .Can some one please advise me on how to set it up so my daughter can use the printer via her PCLinuxOS box ? There seem to be plenty of guides for printer sharing with windows but I haven't come across one for this combination of distros.
Thanks 
Steve

Are both machines using CUPS?

On the Ubuntu box do

[http://localhost:631](http://localhost:631)

Go to 'Administration' and tick 'Share published printers connected to this system'

On the PCLinuxOS box go to the same URL and tick 'Show printers shared by other systems'

Check: lpstat -a on the PCLinuxOS box. Or look under 'Print..' in the browser.

---

### Post by bossa on 2008-04-04
Hi Brian 

Yes I am pretty sure both are using CUPS 

RE:Check: lpstat -a on the PCLinuxOS box. Or look under 'Print..' in the browser. 

Do I do that in treminal? 

Will have to wait until its possible to go on her PC ... shes using it right now and its very difficullt to communicate with her when she is ... if you know what I mean ;)

---

### Post by brian_p on 2008-04-04
> **bossa said:**
> Hi Brian 

Yes I am pretty sure both are using CUPS 

In a terminal:

ps ax | grep cupsd

on both machines will tell you for sure. Look for /usr/sbin/cupsd in the output.


> RE:Check: lpstat -a on the PCLinuxOS box. Or look under 'Print..' in the browser. 

Do I do that in treminal? 

Yes, but checking what 'File/Print..' says won't do any harm and you may feel more comfortable with it.

I've found CUPS to be temperamental at times but the way I've outlined is supposed to work.

---

### Post by bossa on 2008-04-04
Hi Brian 
Managed to turf my daughter off her PC for 5 mins and I followed your instuction and it worked perfectly :)
Thanks very much for your advice 
Steve

---

