---
title: "UBUNTU and HPLASER JET  Printing Problme"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by SheLady on 2007-11-07
I am new in Ubuntu world and trying to do some experimenting in printing.
I got a CD of ubuntu 7.07 and a HP Lasetjet 2420d printer. Now I went to System, Administration, Printing and Add printer, I can add the printer without any problem. The required HPLIP is already installed in the CD < I have checked it via this command.

dpkg -l hplip

the out put is this:

ii  hplip            1.7.3-0ubuntu1           HP Linux

Now the problem is that it shows that the printer is ready and when I send 
the printing it is in the queue but nothing get print !!!!!

What do I do next?

Tnx

She

---

### Post by stchman on 2007-11-07
> **SheLady said:**
> I am new in Ubuntu world and trying to do some experimenting in printing.
I got a CD of ubuntu 7.07 and a HP Lasetjet 2420d printer. Now I went to System, Administration, Printing and Add printer, I can add the printer without any problem. The required HPLIP is already installed in the CD < I have checked it via this command.

dpkg -l hplip

the out put is this:

ii  hplip            1.7.3-0ubuntu1           HP Linux

Now the problem is that it shows that the printer is ready and when I send 
the printing it is in the queue but nothing get print !!!!!

What do I do next?

Tnx

She

According to [www.linuxprinting.org](www.linuxprinting.org) that printer works perfectly.

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2420dn](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2420dn)

---

### Post by john_abq on 2007-11-07
She-

It sounds like the same problem I have with my old Laserjet 4 that is connected to my machine with a parallel-usb cable. 

I found that if I turn the printer on before I turn on the computer the printer will be recognized as being connected.  

If your computer is already on before you turn on the printer. Start your printer and after it boots up, pull the usb/ printer cable out of the computer and then re-insert it again. The computer will now detect the printer. "Hot-pluging" the printer appears to work.

Regards

John

---

