---
title: "[SOLVED] Can't print to printer on xp machine"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by pappo on 2007-03-07
I cannot print on the printer connected to my PC running Windows XP Home Edition.

I am running Kubuntu 6.10 on my second PC.
Linux kubuntu 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

I installed smbfs and winbind.

I used System Settings to configure the printer for an SMB type printer.
When I scanned, it found the hp3940 printer.
When I send the test page, my printer starts making noises like it wants to print something, but it never pulls paper in and starts actually printing.  After about 5 seconds it stops making noise and when I look in Windows print queue, I can see the job there but it will not finish printing.
Also, it locks up my Windows printer so that I can't print anything else.  I cannot delete the job.
I have to reboot the XP machine to clear the printer queue.

On my Linux box, I used to run Ubuntu 6.06 and had not problems at all with the same printer.
The only thing I changed was upgrading to Kubuntu 6.10.

Any help would be appreciated.

Regards,
pappo

---

### Post by j.miller565 on 2007-03-07
Same happens to me but it's on a ubuntu to ubuntu network

---

### Post by j.miller565 on 2007-03-08
anyone?

---

### Post by j.miller565 on 2007-03-08
anyone?

---

### Post by j.miller565 on 2007-03-08
does anyone know anything about this plz

---

### Post by michael.dobrofsky on 2007-09-06
I've got the same prob - no one seems to have any idea or any fix for this :(

---

### Post by ronmarley1 on 2007-09-06
Not sure if you've tried this site yet, but it looks like the printer works when connected locally.  Maybe you can get further assistance there?  Good luck!
[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3940](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3940)

---

### Post by parsu4linux on 2007-09-06
Hello pappo, j.miller565 and michael.dobrofsky,

I am a newbie to ubuntu who has just switched over from the XP world!!! I too faced the same problem. 

This is one area in Linux world, where we to be open (to try things).

I am running HP Deskjet 656C on an XP machine and I am able to print it from my ubuntu 7.04 (Fiesty Fawn).

The first thing I want you to see is that if you are able to see your printer in the list. If you are able to see, then try it one last time (just to check / make sure if it is working the same way).

If it is still making noises and not printing anything, then try to configure a printer which is just one which is close to the series (in my case, I had Deskjet 648C and 660C)

I went ahead with the 660c and it worked!!!

I went through the list of HP Printers available (starting from 3840, 3845, 3920 and 3940) and the nearest I could find was Deskjet 3920 (in the 39XX series, because your printer starts with 39) or you can also try 3840 (because it 3X and ends in 40). But I am not sure with the 38XX series though.

Try 3920. If it is not getting configured, then it's really a problem!!!

All the best.....

---

### Post by dast on 2007-11-20
Same problem with an HP DeskJet 3940 attached to a Windows XP SP2 Home machine from an Ubuntu 7.04 client sending the print job.  Same behavior as described above, printer wizzes a bit, doesn't pull paper, and it leaves the print queue wedged on the XP box.

No solution found yet... : (

---

### Post by pappo on 2008-06-01
On the windows machine, go to the Control Panel and printers.
Select your printer and go to Properties.
Under properties, select Ports and make sure that "bidirectional printing support" is NOT selected.

---

### Post by popaclay on 2008-06-14
mercy saints alive! thank you!

---

