---
title: "Lexmark Optra S printer"
date: 2012-01-01
forum: Apple Hardware Users
---

### Post by phillat5dock on 2012-01-01
I have had some trouble installing my old Lexmark Optra S 1650 postscript printer.

On Mac OS X it works well because Apple has created drivers for it. But in Ubuntu I was stuck using the default driver.

This is a postcript printer so it is capable of loading a ppd file. But there are no ppd files that I could find using Google.

So what I did was copy the ppd from Mac OS X and open it up alongside the default ppd in Ubuntu.

I only had to change/modify a few lines and then I saved the new file into /usr/share/ppd/custom.

Then I installed it using the Cups interface in Firefox ([http://localhost:631/printers](http://localhost:631/printers)) and pointed it at the new ppd.

The only thing left to do is find where the printer device icons are stored in Ubuntu so I can get the correct icon in System Settings/Printing

---

