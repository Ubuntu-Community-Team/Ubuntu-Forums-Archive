---
title: "Printers no longer working in windows (yes I said that)"
date: 2014-04-16
forum: Any Other OS
---

### Post by tleepc on 2014-04-16
Is there a way to make a printer that works with ubuntu, work with windows when there is no longer a driver for it?  Almost like spoofing the printer so windows see another printer over the network and can install the drivers on it?  Right now I have an Imagistics printer IM510/IM4510 also known as a sharp ARM450. There are no windows 8 drivers, and the suggestion for installing the old drivers on a windows 8 computer doesn't work, get so far then repeats.  However, I have the printer installed on Ubuntu as Generic PCL 6 Driver, and it works well .  I can get a generic text to work with windows, but the printer needs to do images.  Any help or suggestions would be great. And I know this is an Ubuntu area, and I am sorry for any insults I may have caused. I, by the way, hate windows.

---

### Post by slickymaster on 2014-04-16
Since the question addresses Windows it's moved to Other OS/Distro Support sub-forum.

---

### Post by SeijiSensei on 2014-04-16
If the Ubuntu box is using CUPS with a working driver, you can install a Postscript driver on the Windows machines and talk to the CUPS server that way.  I've used the [Apple PS driver]("http://www.adobe.com/support/downloads/product.jsp?product=pdrv&platform=win") in Windows for this task.  Windows supports the "Internet Printing Protocol" which CUPS also uses.

You may need to fiddle with CUPS on the Ubuntu box to make sure it is listening to the machine's network interface.  I believe that, by default, CUPS only listens on localhost (127.0.0.1) for security reasons.  Make sure that you only have 
```
Listen 631
```
in cupsd.conf rather than a definition that includes both an IP address and port 631.

---

### Post by tleepc on 2014-04-17
Thank you for the response, however, I am not finding the apple PS driver for windows 2012 or 8.1.  Just keeps coming up with this app can not run on your computer.  I also tried to do a compatibility mode, as well as extracted the files myself to try to get it to work.  Have I mentioned, that I now and for ever more, hate Microsoft!

---

### Post by SeijiSensei on 2014-04-17
I browsed around my Win7 installation and noticed how few printer drivers now ship with Windows.

In the "Generic" category, there is a driver called "[35PPM PS]("http://answers.microsoft.com/en-us/windows/forum/windows_7-hardware/looking-for-the-universal-postscript-windows/dccc996a-ff2f-4efa-a2b9-4c5a2c94cf11")."  Maybe that will fix the problem.

---

### Post by tleepc on 2014-04-18
I wish, I think I am just going to hit all the generic ones, because on the server (2012) its not even listed. Even after I tell it to look for windows updates. I also have a shout out to the companies, no response.  I hope to hear something.

---

### Post by tleepc on 2014-04-22
Ok, Ok,  So A big shout out and thank you for the help.  What I ended up finding out was that the cannon driver (image runner) works with this printer.  The only way I figured that out was a hapinstance.  I figured when I did a search for Imigistics and it would bring up the cannon websight I would try that out. I hope that anyone else out there looking for this will come across this board.  Cause this one was a headache.

---

