---
title: "wireless printing to usb printer on winxp box"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by jjf on 2006-03-06
My setup: a Canon i550 connected via USB cable to a Windows XP box.  I want my Ubuntu laptop to be able to print wirelessly over the network.

I've got the wireless part working (2 more miracles and I'm eligible for sainthood).  I'm able to add the printer in Ubuntu, and even send a document to it.  

The printer prints the first page of any document I send it.  The document remains in the print queue on the Windows box, but my Ubuntu laptop doesn't see it in the queue.  It will sit idle for 10 minutes, then print the second page.  Idle for 10 minutes more, then the third page.  I assume it would continue like this for larger documents.

My search of the forums makes it look like USB printing is a problem.  Am I just out of luck, or is there some fix for this?  Thanks.

---

### Post by mr.p on 2006-03-06
[QUOTE=jjf]My setup: a Canon i550 connected via USB cable to a Windows XP box.  I want my Ubuntu laptop to be able to print wirelessly over the network.

I've got the wireless part working (2 more miracles and I'm eligible for sainthood).  I'm able to add the printer in Ubuntu, and even send a document to it.  

The printer prints the first page of any document I send it.  The document remains in the print queue on the Windows box, but my Ubuntu laptop doesn't see it in the queue.  It will sit idle for 10 minutes, then print the second page.  Idle for 10 minutes more, then the third page.  I assume it would continue like this for larger documents.

My search of the forums makes it look like USB printing is a problem.  Am I just out of luck, or is there some fix for this?  Thanks.[/QUOTE]

Quick suggestion, have you tried the same but over ethernet? Same problem?

---

### Post by learning curve on 2006-03-06
Try these instructions.  it should work for you.

Make sure you have Samba installed.  You can get it using the Synaptics Package Manager.
Enable “Print Services for Unix” on Windows XP machine and share printer.  Right click on the printer and click on sharing and then click in the radio button that says share this printer. (I’m not actually sure that this is necessary, it might be a red herring…) read the 2nd from the bottom sentence.
When you add the printer in Ubuntu, 
1.Choose “Network Printer” and “Windows Printer (SMB)” 
2.put your Workgroup in the Host field usally it is MSHOME by default
3.Put “guest@<IPadress>/<printer>” in the Printer field (replacing <host> and <printer> with your host & printer names) 
So, for example,  your printer was called “LaserPrinter”, you would put guest@ipaddress/LaserPrinter.
You should not need a name and password for the Windows machine for this to work. 
You also have to go to Control Panel/add/remove programs and add a windows component to accept print services for UNIX.  Check the box Other Network and File Print Services click next  and it will install.  Reboot

to find the IP address on your windows machine go to RUN and type in cmd/hit enter/when the dos window opens type in ipconfig and hit enter.  you should now see your IP address as xxx.xxx.xxx.xxx

good luck,
Learning Curve:cool:

---

### Post by jjf on 2006-03-06
Thanks for helping.

I did what you suggested, Learning Curve, and got the same behavior.  First page printed, but the second one did not (I haven't yet waited 10 minutes to see if it will eventually come out).

Maybe I need a different driver?  When I went through Ubuntu's printer wizard and told it I had a Canon S450 (the sister-model to the i550), it would print both pages, but print them very small in the top left corner.  With the BJC-7000 driver, it prints regular size, but only one page.

Any other suggestions?

I'll try the wired connection tomorrow.

---

### Post by jjf on 2006-03-06
Aha!  I got it! \\:D/ 

There are two drivers in the list: BJC-7000 (with a dash) and BJC 7000 (with no dash).  I had the dash one and it wasn't working.  I needed the no-dash one.  :-? The no-dash one uses a driver called "The Gimp (something something)."  the dash one uses a driver called "bj800" or somesuch.

Thanks for the help.

---

