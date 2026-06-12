---
title: "Problem with USB--Parallel Adapter"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Tahi_Kiwi on 2007-01-12
Version: Ubuntu 6.06
Running Ubuntu as Guest OS on VMware Workstation 6 BETA as well as booted off from Ubuntu CD.

PC lacks a parallel port, so I bought an Inland brand USB-to-Parallel cable to connect to my HP LaserJet 4200. This adapter cable works perfectly under host OS Win XP.

However, from either config of Ubuntu--as OS guest through VWware Workstation or directly from Ubuntu boot CD, attempts to print to LaserJet fails. Nothing happens. 

I can display the Printing dialog box by clicking the Printer icon in Ubuntu. Two jobs are just sitting their with Pending status. The option to Resume printing is greyed out. Only the option to Cancel is available from the menu.

Discussed with VMware BETA support staff, and given that printing fails BOTH within VMware Workstation and bypassing VMware (direct CD boot), they referred me to Ubuntu for support. 

I have unplugged and replugged the USB cable, but that made no difference. Again, it works perfectly under Win XP, regardless.

Can you help? Should I put this issue in another of this forum? I am a newbie to Ubuntu.

MicroCenter carries the Inland brand USB - Parallel cable for about $10.

Thanks.

---

### Post by saadakhtar on 2007-01-12
please post the results for [COLOR="Red"]**lsusb**[/COLOR]

---

### Post by Tahi_Kiwi on 2007-01-13
Results for lsusb are:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by Tahi_Kiwi on 2007-01-17
Hello, hello...does anyone have ideas, please?

Thank you.

---

### Post by Tahi_Kiwi on 2007-01-18
OK, while we're awaiting assistance or ideas, I've been trying to troubleshoot further.

I booted up the Ubuntu CD on a computer with a parallel port, to which another LaserJet printer is connected.

I followed the procedure to Add Printer.
It automatically recognized HP LaserJet 4050.
For driver, I tried both lj4-something and the first one on the list (forgot name ljissomething).
RESULT: After completing the process to add printer, I waited and waited and waited. No printer icon for the LaserJet ever appeared. I rebooted for good measure, but still no printer listing or icon. 

I opened up Text Editor, typed some garbage text, and tried to print. RESULT: No LaserJet appears on the Dialog box--only PDF and Postscript, I think. 

It's the same symptom as my other PC (the one with the USB>Parallel adapter). 

Ideas, please? Thank you

---

### Post by Tahi_Kiwi on 2007-01-24
Hello, hello...

Can I be the only one having this problem?

Although I am a noob, perhaps I should post this issue elsewhere on this forum? 

Two different computers fail to work with printing. One is connected with parallel port; the other uses a USB > Parallel adaptor. 

Ideas, please, please, please? 

Short of any resolution, do you have recommendations for some other flavor of Linux that works well with noobs and printers???

---

### Post by wadesmart on 2007-07-15
Your not the only one having troubles.

I have a LaserJet 4050 but Im trying to go only parallel as I have not a parallel to usb cable. I can see the printer icon, can access the printer via right clicking on the icon but I cant get the paper to print. 

wade

---

### Post by wadesmart on 2007-07-16
This is what I have done so far so you might see what it does for you.

echo -ne '\f' >/dev/lp0
Do this as sudo. This should print out a page. For me, it just spools up and spits out a single page with nothing on it. 

Under Properties for the printer, it was suggested I have "High Quality Image (Gutenprint CUPS) (expert) driver checked. 

Also, hpijs, hplip, and hplip-data need to be sure to have installed. I think they are by default though. 

wade

---

