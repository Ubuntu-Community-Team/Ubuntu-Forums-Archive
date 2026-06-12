---
title: "trouble printing in clipper when using freedos"
date: 2015-09-18
forum: Any Other OS
---

### Post by KayeNg on 2015-09-18
Hi guys. Apologies if this is not the right forum to post my problem.

I have a desktop  computer with a motherboard that has a built-in parallel port.  When I  boot into FreeDOS and run an old Clipper program, the program can print  just fine, without editing any system files.  It just works.

I  have another desktop computer in which the parallel port is an  expansion, not built-in with the motherboard.  Upon printing using  Clipper program, I get:
Error: Term/0
Quit / Retry
Something like that.  It cannot print.

I wonder if this is the answer:
[http://help.fdos.org/en/hhstndrd/base/printer.htm](http://help.fdos.org/en/hhstndrd/base/printer.htm)
If it is, please help. I don't quite get it.

Other info that may or may not be relevant:
-- I believe the installed freedos is 1.0 , not the latest.
--  When running the Clipper program in Windows 7 via command prompt, I can  print.  However, I had to go to Control panel, View devices and  printers, right-click the printer (epson LX310) , Printer properties,  Ports tab, Enable bidirectional support and enable printer pooling,  checked LPT1, LPT2, and LPT3.  That made it possible for me to print in  Clipper program.  Before doing all of that, I get an error like it  cannot communicate with the printer.

Summary: Parallel port  is only an expansion.  Using Clipper in Windows 7 command prompt, it  can print.  Using Clipper in FreeDOS, I get Error: Term/0

Thank you so much!

---

