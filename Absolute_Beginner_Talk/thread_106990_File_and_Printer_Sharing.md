---
title: "File and Printer Sharing"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by akniss on 2005-12-22
Howdy.  Does anyone know of a good file and Printer sharing HOWTO? I'm especially interested in printer sharing from a Ubuntu box to another ubuntu machine and XP machine. I've searched the wiki and these forums for printer sharing, and the results are either too specific for certain configurations, or too technical for a beginner to follow.  I just put Ubuntu on my old P3 desktop to use as a file/print server, but can't figure out how to print to it from my Ubuntu laptop or my wife's XP laptop.  I can exchange files from the Ubuntu laptop to the Ubuntu desktop after following some howtos, but still can't print.  Maybe we can post links in this thread to HOWTOs and threads with good solutions.  It seems to be an often asked question, but with few satisfactory answers.

---

### Post by akniss on 2005-12-22
If I can sort through some other results and get things working, I can try to piece together a HOWTO from my experience here.

---

### Post by Buffalo Soldier on 2005-12-22
For printer sharing from a Ubuntu box to another ubuntu box using CUPS, try viewing this thread -->> [http://ubuntuforums.org/showthread.php?t=93328](http://ubuntuforums.org/showthread.php?t=93328)

---

### Post by akniss on 2006-01-01
How about sharing a printer hooked to a ubuntu box with a windows box using samba?  And connecting another ubuntu box to the same network?

---

### Post by fishfillet on 2006-01-01
Here's my how-to on my blog: [http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)

I hope it helps!

---

### Post by akniss on 2006-01-02
Thanks fishfillet.  That one looks helpful.  I haven't quite got mine working yet, but I'm closer than I was a few days ago.  

Doesn't anyone have any other good HOWTOs out there?  This seems like a pretty common thing that a typical user would want to do.  Surely there are a couple floating around out there?!?

---

### Post by mistergq on 2006-01-02
Here is a how to that I wrote a while ago - sorry, it is not too detailed, but hopefully it will get you in the right direction:

I am using a LJ1200 printer.  It is connected to my Wife's Windows computer.  

I went into Network Property, changed her computer from IP selection with DHCP to manually configuring everything - meaning I assigned it an IP address and entered the DNS server information for my ISP - ConCast.  I also reminded myself what i named the printer.

Then on the computer running Ubuntu, I went to System -> Adminstration -> Pri nter, clicked on New Printer, changed it from local printer to network printer, changed the pull down to Windows Printer (SMB), typed in her ip address, printer name, downloaded the driver from [http://www.linuxprinting.org](http://www.linuxprinting.org).

That seems to be about it and it worked.

Hope that helps.

---

### Post by bdd4 on 2006-01-04
this worked for me. it is from chris who was having the same problem:

EUREKA! - THE FOLLOWING WAS THE SOLUTION! - IT WORKS LIKE TEXTBOOK!:

IMHO, sounds like you may not have turned on the printer sharing option. See this thread for printer sharing [http://www.ubuntuforums.org/showthre...=printer+share](http://www.ubuntuforums.org/showthre...=printer+share)

bdd4

---

### Post by akniss on 2006-01-04
[QUOTE=bdd4]this worked for me. it is from chris who was having the same problem:

EUREKA! - THE FOLLOWING WAS THE SOLUTION! - IT WORKS LIKE TEXTBOOK!:

IMHO, sounds like you may not have turned on the printer sharing option. See this thread for printer sharing [http://www.ubuntuforums.org/showthre...=printer+share](http://www.ubuntuforums.org/showthre...=printer+share)

bdd4[/QUOTE]

That link didn't work for me...  I get a 404.

---

