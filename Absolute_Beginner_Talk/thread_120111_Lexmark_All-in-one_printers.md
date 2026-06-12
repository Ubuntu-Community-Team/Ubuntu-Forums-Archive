---
title: "Lexmark All-in-one printers"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by DMorton3 on 2006-01-20
Has anyone tried and succeded using the Lexmark Linux Printer Driver Development Kit found at this link [http://www.lexmark.com/uncomplicate/sequentialem/home/0,7070,204816596_478052506_0_en,00.html](http://www.lexmark.com/uncomplicate/sequentialem/home/0,7070,204816596_478052506_0_en,00.html)

Being new to Linux ( 1st time user ), I am unfamiliar with most of what I read on their link, but if someone has a how-to or can just tell me it works...I will be willing to dive in.

Thanks :D

---

### Post by borisattva on 2006-01-21
try a simpler approach first: 

go to System > Administration > Printing and run the Add printer wizard.

with luck your printer model will be listed there explicitely.

note however not to rush witha 'closest match' as using z42/51 did not work with my z52, infact made it unsuable completely untill i reinstalled. uintill i found the explicit z52 which was just named a little differently and escaped my notice.

if that doesnt work hopefully someone else will answer with more help,
i'm a newb to this myself :)

welcome to the board

---

### Post by diggs on 2006-01-21
funny, I'm doing the same thing with an HP. works dandy on my laptop, but the desktop is giving me no love. hopefully someone will help me out in my very own special thread!

---

### Post by Lunixfanboy on 2006-01-21
The Lexmark kit you linked to is a collection of libraries which allows folks to write drivers to work with the Lexmark doorstops, er, printers. Lexmark has for quite some time been very much less than forthcoming with drivers for Linux for ANY of their printers, much less the All-in-Ones. Sorry to rain on the parade, though.

---

### Post by DMorton3 on 2006-01-21
well leave it to lexmark to do a job the job half the way.  Funny when I bought this printer I started to go HP...wish I would have stuck to that.   BTW, loving linux so far.  Haven't given up the windoze because of the gaming and the on line banking in quicken, but once that it is remedied I will be a true convert.

---

### Post by borisattva on 2006-01-21
in lexmarks defence i think they have a pretty good design for the money.
and actually they are on the better end of printer designers in regards to linux drivers.  granted they mainly provide RPMS for redhat based distros', thats still better than nothing.
and with a little reserach you can learn how to convert those to a debian based distro like ubuntu.

you definietly do not need the developer kit. just search lexmart site with your printer model and download the driver RPM and then use ALIEN to convert it to deb.

---

### Post by Sef on 2006-01-21
> granted they mainly provide RPMS for redhat based distros', thats still better than nothing.

Too often Lexmark provides no drivers for Linux.  That's the problem with Lexmark, Canon and some other companies.  Best to stick with either HP or Epson, unless you check out first if there are drivers for your printer.

---

### Post by debernardis on 2006-01-21
If you own a P3150 all-in-one or similar (Z700, Z705, Z708, P706, Z707...), just try here: [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)
Worked for mine.

---

