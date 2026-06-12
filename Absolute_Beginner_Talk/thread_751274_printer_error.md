---
title: "printer error"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by boywholinuxed on 2008-04-10
hi
i got a hp f41000 printer.
when i try to print a document the following error comes:

Printer 'Deskjet_f41000_series':'other'.
what is the source of this error and wat can i do about it?

---

### Post by amazingtaters on 2008-04-10
Allright, could you provide a little bit more info. For instance, is the printer set as your default? Do you have the hplip drivers installed?

---

### Post by boywholinuxed on 2008-04-10
yeah it is my default printer because it si the only one.

About the driver,i think it must be there because i could take printouts earlier,this error comes only occasionally and then when i restart the  machine and try it prints fine.But of late the error keeps coming despite me restarting and trying at least 3 times.

---

### Post by amazingtaters on 2008-04-10
Well the cups (Common Unix Printer System I believe is what it stands for, or something like that) system is the default for handling printers. I had some problems with my hp 4100 series with the cups drivers. Just so to synaptic and search for hplip, and install the hp drivers, and the hplip toolbox. That way you'll get a gui that you can control your printer from, get the status for and everything. That should solve your problem.

---

### Post by stchman on 2008-04-10
> **boywholinuxed said:**
> hi
i got a hp f41000 printer.
when i try to print a document the following error comes:

Printer 'Deskjet_f41000_series':'other'.
what is the source of this error and wat can i do about it?

I found an entry for a DeskJet F4100 at openprinting.org

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_F4100](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_F4100)

It is reported to work mostly using the hpijs driver.

---

### Post by boywholinuxed on 2008-04-11
hi,
i made a mistake ,my printer is actually hp deskject f4180,i meant that my printer was in the f4100 series and not actually f4100 itself!

---

### Post by boywholinuxed on 2008-04-11
after installing hplib how do i access it?i mean where to find it?

---

### Post by boywholinuxed on 2008-04-11
i think i have hplib by default,its represented by a small printer icon next to the date and time ,right?

---

### Post by boywholinuxed on 2008-04-11
i installed hplip

and went to hp device manager:it said paper or catridge or paper jammed.i checked the paper it was not stuck and the catridge seemed to be in its place and it was not stuck as well!

the printer icon at the side of my taskbar still says the same thing printer'deskejet_f4100_series_:'other'

---

### Post by boywholinuxed on 2008-04-11
i am thinking of uninstalling the device and reinstalling it,do u think thats a good idea?

---

### Post by boywholinuxed on 2008-04-11
hi  guys,
thanks for you consideration but i managed to solve it on my own.I think the problem was that i was trying to hurry and as a result printing queue got bigger and bigger.I cancelled all the tasks ,gave each print request one by one slowly and voila it comes out fine!!

the problem is that in windows printing gets done quickly but here it takes time.Also the support is more for windows than ubuntu,maybe in ubuntu 8.4 or 9.8 something can be done about it!!!

anyways still ubuntu is way ahead of windows without a doubt!

---

