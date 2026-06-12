---
title: "Deskjet not detected"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-10-28
I have a deskjet 960C connected to my parrallel port that worked with dapper.  Now that I upgraded to edgy I am not able to auto-detect my printer.  I tried to do it manually and when I try a test page it says 1 page printing on the printer but nothing. 

I have tried the linuxprint.org and when I run the .run file it just hangs up ever time.


If anyone has some suggestions I would appreciate it.

---

### Post by Thokk on 2006-10-30
I had the same problem with a HP 952C.  I've managed to mostly work around the problem but it is an imperfect solution (see below).

If you want to try it, here is what I did:
  -goto System > Administration > Printing
  -right-click on your printer and select preferences
  -goto the Connection tab
  -below the auto-detected printers is the "use another printer by specifying a port" option and a drop-down box that (for me defaulted to "hp:/no_device_found"  Select that option and change the box to "LPT #1" (or possibly a different LPT number if you have multiple parallel ports).

At this point my printer started working, and I can print from programs and the command line.  There are still no auto-detected printers and the HP printer utility (HPLIP) doesn't recognize that I have a printer installed, but it does show up in [http://localhost:631/printers](http://localhost:631/printers)

So in short it works in the most important ways, but if someone has a better solution I'd like to hear it.

---

### Post by raqball on 2006-10-30
Here is the info on your printer from Linuxprinting.org

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_960C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_960C)

---

### Post by gentlemanmasher on 2006-11-13
> **Thokk said:**
> I had the same problem with a HP 952C.  I've managed to mostly work around the problem but it is an imperfect solution (see below).

If you want to try it, here is what I did:
  -goto System > Administration > Printing
  -right-click on your printer and select preferences
  -goto the Connection tab
  -below the auto-detected printers is the "use another printer by specifying a port" option and a drop-down box that (for me defaulted to "hp:/no_device_found"  Select that option and change the box to "LPT #1" (or possibly a different LPT number if you have multiple parallel ports).

At this point my printer started working, and I can print from programs and the command line.  There are still no auto-detected printers and the HP printer utility (HPLIP) doesn't recognize that I have a printer installed, but it does show up in [http://localhost:631/printers](http://localhost:631/printers)


So in short it works in the most important ways, but if someone has a better solution I'd like to hear it.

This is how I got mine to work as well.  It autodetected in dapper but not edgy.  Oh well it works now.  Thanks all for the help.

---

### Post by h2gofast on 2006-11-23
I have an hp deskjet 842c and this worked for me as well.

For the record it was detected and easily setup under Dapper.  The upgrade to Edgy lost it.

---

### Post by Jennabob on 2007-03-19
Thank you for this post it really helped! :biggrin:

---

### Post by oilchangeguy on 2007-03-19
was there a problem with 6.06? remember it's going to be supported until 2009. and 6.10 is only going to be supported until 2008.

---

### Post by 11hjpphty76lkjj on 2007-03-23
The Deskjet 960c is supported by HPLIP.

[http://hplip.sf.net](http://hplip.sf.net)

---

