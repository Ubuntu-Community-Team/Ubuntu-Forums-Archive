---
title: "apple client to ubuntu printer server"
date: 2010-12-11
forum: Apple Hardware Users
---

### Post by matamoscas on 2010-12-11
This shouldn't be as hard as it's proving to me =(

Apple developed CUPS? What gives...

Ok, here's the skinny.

I got a Ubuntu 10.04 system setup with a printer.
A. I can print to this printer. Check.
B. I can print to this printer from a Windows client.
C. I cannot for the life of me figure out how to get a mac OS X 10.6.5 client
to work. Argghhh.

The closest I got was setting up Cups from the apple client, and printing a test page from the CUPS webpage.  Nothing else.

I have tried just about everything, forwards and backwards.  I get almost always the same result.

My printer pauses when I try to print to the server -- I hit resume, it pauses. It just doesn't complete a single job.

Any help would be greatly appreciated. Anyone have any experience with this??

thanks,
matt

---

### Post by DumbledoreMD on 2011-02-15
I'm having the exact same issue.. When i try to print from a mac os x laptop it just says "error 603".. are there any solutions to this?

---

### Post by DukeTate on 2011-07-28
Same issue here... and it used to work fine in the previous release of Ubuntu!?

---

### Post by drdos2006 on 2011-07-28
Originally Posted by hidesertmlb in the Server Section

1- in /etc/samba/smb.conf ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page 

regards

---

