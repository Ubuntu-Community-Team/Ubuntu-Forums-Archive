---
title: "epson CX3810 problem"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2006-12-30
I've recently installed Ubuntu and the only problem (that I can see) is that my Epson all-in-One CX3810 doesn't work.  Printer is found but job stays in queue forever.

I don't know if scanner works since I'm not clear on how to use it yet.
:???:

---

### Post by Sef on 2006-12-30
> I've recently installed Ubuntu and the only problem (that I can see) is that my Epson all-in-One CX3810 doesn't work. Printer is found but job stays in queue forever.

I don't know if scanner works since I'm not clear on how to use it yet.

For the printer, System > Administration > Printing.   After choosing your printer, **click Foward**, not install.  

For your scanner, Applications > Graphics > Sane Image Scanner.   It should work.

---

### Post by jgf621 on 2006-12-30
Thank you.  Printer now works fine.  Sane, however tells me that there are "no devices found".
:???:

---

### Post by Sef on 2006-12-30
I found this on [Opensubscriber]("http://www.opensubscriber.com/message/uug-list@uug.byu.edu/3583822.html") about the cx3810:

> The scanner side required two configs.  I had to put the vendor id and  
product id (which I found on google!) into the sane configuration file  
and then I had to edit the hotplug file /etc/hotplug/usb/libsane.usermap  
to make sure it had a line with the vendor and product ids so that  
the /dev entry would be set up properly.  Then it just worked.    

You will need someone with a bit more experience than me to tell you exactly what to do.

---

### Post by jgf621 on 2006-12-31
Sane Help tells me I may want to try it in /root.  I tried this via sudo and got the most frightening message that it was extremely dangerous and I would be ALONE.  I'm not experienced enough to evaluate the risk.

Advice, pls.

---

### Post by chuvisco on 2007-01-03
> **Sef said:**
> I found this on [Opensubscriber]("http://www.opensubscriber.com/message/uug-list@uug.byu.edu/3583822.html") about the cx3810:



You will need someone with a bit more experience than me to tell you exactly what to do.

Here is how you do this (I owe this to mrcaseyj on [this thread]("http://www.ubuntuforums.org/showthread.php?t=121540&page=2&highlight=epson+cx3810+scanner")):

Open a terminal and run

```
sudo gedit /etc/sane.d/epson.conf
```

We need to add the line 

```
usb 0x04b8 0x0818
```

 to this file.  I put it down towards the bottom like this:

```
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
usb 0x04b8 0x0818
```

Then save your changes and exit.  After making this change, my scanner is working perfectly.  Please note that I am running Edgy and additional steps may be required for previous releases.

Note to those that have had problems with this printer/scanner in the past: Scanning and printing is working (at the same time! :o ) and I did not have to change permissions on any files.  The usb line above should work if you have the CX 3810; if it is not working or you have a slightly different model, you could install sane-utils and then run sane-find-scanner as described in mrcaseyj's post.

---

### Post by jgf621 on 2007-01-03
Thank you!  Adding that line gets the scanner recognized.

One problem remains.  I can't seem to change the size of scan area.  It is grayed out at 0.59 x 0.16 in.  Am I missing something here?

:-D

---

### Post by jgf621 on 2007-01-03
OK, now I see it.  I have to do the preview first and that defines size.

Thanks again for the good advice.  This has taken me more than a week to figure out.

---

### Post by chuvisco on 2007-01-03
> **jgf621 said:**
> This has taken me more than a week to figure out.

Yes, I saw a couple of your posts when I was researching this myself.  Glad to hear that it worked for you.

---

### Post by trents on 2007-01-26
Thanks, chuvisco. 

Your instructions work for Dapper too. Although, I found I had to restart the PC for it to take. Before I did that Xane locked up when I clicked on the preview button.

Steve

---

### Post by nutz on 2007-06-02
> **chuvisco said:**
> Here is how you do this (I owe this to mrcaseyj on [this thread]("http://www.ubuntuforums.org/showthread.php?t=121540&page=2&highlight=epson+cx3810+scanner")):

Open a terminal and run

```
sudo gedit /etc/sane.d/epson.conf
```

We need to add the line 

```
usb 0x04b8 0x0818
```

 to this file.  I put it down towards the bottom like this:

```
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
usb 0x04b8 0x0818
```

Then save your changes and exit.  After making this change, my scanner is working perfectly.  Please note that I am running Edgy and additional steps may be required for previous releases.

Note to those that have had problems with this printer/scanner in the past: Scanning and printing is working (at the same time! :o ) and I did not have to change permissions on any files.  The usb line above should work if you have the CX 3810; if it is not working or you have a slightly different model, you could install sane-utils and then run sane-find-scanner as described in mrcaseyj's post.

Worked for me too; CX3810 now scans...

---

### Post by voodoo_chicken1 on 2007-10-30
My setup is different: I'm sharing the printer on an Apple Airport Extreme Base Station.  I got it to print wirelessly from my Macbook Pro and my PC running Ubuntu that is hard wired to the basestation.  Now I'm trying to get it to scan but no luck.  Should I be doing something differently?  IP address and port specified somewhere?

---

