---
title: "HP Laserjet printing problems"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by don_c on 2006-04-05
I am trying out Ubuntu on an old PC on our company network.  Everything is working out well but I have problems printing.  The printer is a HP Laserjet 4 plus on the network.  Printer has installed OK and says "Ready" in the printer page, but when I do a test print I don't get the correct output.  Instead I get:

%!
%% %%
<</ManualFeed false>>setpagedevice
%!PS-Adobe-3.0
%%Requirements: duplex 

etc.etc.......

Any ideas???

---

### Post by don_c on 2006-04-05
Found the answer in the "similar threads" box at the bottom....

Changed the driver from the suggested to "hpijs".

---

### Post by _simon_ on 2006-04-05
Just a note... I have the same printer and found that it would only work properly with the postscript driver available from here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus)

The other drivers either corrupted the output, did nothing or printed blank pages after each successful print.

---

