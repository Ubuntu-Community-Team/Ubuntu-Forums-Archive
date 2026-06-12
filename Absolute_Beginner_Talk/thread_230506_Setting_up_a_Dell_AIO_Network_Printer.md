---
title: "Setting up a Dell AIO Network Printer"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-08-06
Hi all, I have been using ubuntu for quite a while now and I love everything about it except for one thing, and one thing only. I need to setup my Dell Photo AIO Printer 944. I was told by Dell it is a rebranded Lexmark X2470, which I know Lexmarks are hard to setup but I really need it! :rolleyes:  It is Connected to A Dell 3000 Printer adapter, which will probsbly make it that much harder to setup! ;)  I have it connected to the other 5 Windows PC's in my house but I really need it on this one! If anyone could help me I would really appriciate it! Thank you! :D :D \\:D/

---

### Post by GStubbs43 on 2006-09-04
Well, it has been about a month, so I think it has been long enough for me to BUMP this... :) ](*,) 

Anyone??? This is the *Only* thing that is keeping me from removing Windows and I hate having to restart **every** single time I need to print something... Anyone???!?!?!? :confused:

**1 Day Later:**I'm taking this as a no.

---

### Post by GStubbs43 on 2006-09-11
Okay, will installing VMware +  Windows let me install the drivers for it, or does that use the ubuntu drivers?

---

### Post by gdoermann on 2007-05-29
I have this same printer as well, and I have had a WORLD of problems with it.  The following site gives reasons why it doesn't work:
[http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_944]("http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_944")
I have read that you can get Windows (Full, not emulator) to work in Ubuntu ([http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209") but it says that you cannot get hardware to work that doesn't work on Ubuntu, but then says that the device must be detected on Ubuntu to work.  My printer is detected, but it won't work because it doesn't have the driver.  I will be trying to setup windows within Ubuntu and then setup the driver.  I'll get back to you when I figure it out.

---

### Post by Terl on 2007-05-29
Which dell all in one do you have?  I have the 922 and it shows as a paperweight as does the lexmark equivelant.  I am still playing with some of the lexmark drivers in hopes of getting the printer part to work.

Not all printers will work with Ubuntu (or Linux for that matter) as some manufacturers do not support Linux very well, if at all.  Also, many manufacturers made printers rely on windows for much of its processing in an effort to keep the cost of the printer down.  We are paying for that.  It is much akin to the problems with winmodems....

So, what did I do?  I kept windows xp on my pc and I jut move documents to the shared space and print from xp.  I am still working on getting it going and also hoping Dell will support the printers more now that they are selling pc's with Ubuntu.  If that doesn't happen I will just go buy a supported printer.

Check here for more info:  [Lexmark Printers]("http://openprinting.org/printer_list.cgi?make=Lexmark")  The site is very good for info on printers and whether they work in Linux (and to what degree if they do).

---

### Post by gdoermann on 2007-05-29
> **Terl said:**
> Which dell all in one do you have?  I have the 922 and it shows as a paperweight as does the lexmark equivelant.  I am still playing with some of the lexmark drivers in hopes of getting the printer part to work.

Not all printers will work with Ubuntu (or Linux for that matter) as some manufacturers do not support Linux very well, if at all.  Also, many manufacturers made printers rely on windows for much of its processing in an effort to keep the cost of the printer down.  We are paying for that.  It is much akin to the problems with winmodems....

So, what did I do?  I kept windows xp on my pc and I jut move documents to the shared space and print from xp.  I am still working on getting it going and also hoping Dell will support the printers more now that they are selling pc's with Ubuntu.  If that doesn't happen I will just go buy a supported printer.

Check here for more info:  [Lexmark Printers]("http://openprinting.org/printer_list.cgi?make=Lexmark")  The site is very good for info on printers and whether they work in Linux (and to what degree if they do).

Although, it doesn't fit here, how do you setup the shared space?

---

### Post by Terl on 2007-05-29
> **gdoermann said:**
> Although, it doesn't fit here, how do you setup the shared space?

I use ntfs3g to access my windows xp portion.  I initially made winxp and an extra ntfs portion on one drive (ubuntu is on the second), but with ntfs3g you could just use your exisiting windows space (maybe make a folder just to stay organized).

If you want ntfs3g it is in synaptic.  Search for ntfs3g.  Get it and ntfs-config as well.  When done use the config tool to set up the shares.

---

