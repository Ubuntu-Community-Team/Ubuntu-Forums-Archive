---
title: "Sharing A Printer (Ubuntu 7.04 &amp; Vista)"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-10-08
I'm trying to share a printer that's wired to my Ubuntu desktop. I want my Vista desktop & Vista laptop to be able to use that printer as if they are both wired to those printers.

My Vista can't find the printer, is there a workaround on this one? The XP guide doesn't apply to Vista.

---

### Post by w7kmc on 2007-10-08
I guess cups should be able to be set up as a print server...have you tried that? I never did it myself...but here is a link for setting up a cups server: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Never used Vista...but adding a network printer may be some similiar setup in vista...

---

### Post by P4rD0nM3 on 2007-10-08
That was the one that doesn't work. Because when you choose ADD NETWORK PRINTER, it will automatically try to find it...and when it can't find it, you can't click NEXT. That's where the problem is.

---

### Post by strabes on 2007-10-08
Make sure the printer is shared on the ubuntu box. Run "ifconfig" and look for the section that looks like this:> inet addr: xxx.xx.xx.xxxWrite that IP address down. On the vista computers you can simply add the printer using an http address:> [http://ip.of.ubuntu.box:631/printers/nameofprinter](http://ip.of.ubuntu.box:631/printers/nameofprinter)

---

### Post by P4rD0nM3 on 2007-10-09
> **strabes said:**
> Make sure the printer is shared on the ubuntu box. Run "ifconfig" and look for the section that looks like this:Write that IP address down. On the vista computers you can simply add the printer using an http address:

How do I add the http address in Vista? That's the problem I'm having.

---

### Post by P4rD0nM3 on 2007-10-09
Nevermind! I got it to work! I keep typing 192.168.1.100...I should have typed 192.168.0.100.

---

### Post by pssturges on 2007-10-15
Hi,

I also have a printer connected to an Ubuntu 7.04 box. I have been able to set it up so that I can print remotely from XP & Ubuntu Machines. However, I'm having trouble with my Vista laptop. I assume that on the Vista end it needs to be connected as a web services device. When I try this, I get the error that it could not contact the printer, check address etc. Am I going about this the right way or not?

Thanks
Phil

---

### Post by pssturges on 2007-11-04
Still can't get this working.:mad: I can print very nicely from my ubuntu & xp machines, but I can't seem to be able to add the printer on my vista laptop. I'm trying to add the printer by using "Add a printer using a TCP/IP address or hostname". Then under host name I put "http://192.168.0.10:631/printers/Lexmark", which should correspond with the printer I want to use. It then tries to contact the printer but fails saying that "the device is not found on the network"

Any help much appreciated
Phil

BTW: It's Vista Home Basic if that makes any difference.

---

### Post by pssturges on 2007-11-05
Bump!

---

### Post by stedly on 2008-01-17
Have you tried enabling LPR in windows vista. 

In the Control Panel ->Program->Turn windows features on or off ->print services

Vista just had to come in and make things more complicated.

---

### Post by EXCiD3 on 2008-01-17
I had a problem like this with my HP wireless printer...they only way i could get windows to detect the printer was to use the official drivers. The ip address had changed after a power outage had reset the router and i was forced to reinstall the drivers in order to get the printer back up and running.

---

### Post by stchman on 2008-01-17
> **P4rD0nM3 said:**
> I'm trying to share a printer that's wired to my Ubuntu desktop. I want my Vista desktop & Vista laptop to be able to use that printer as if they are both wired to those printers.

My Vista can't find the printer, is there a workaround on this one? The XP guide doesn't apply to Vista.

I have a tutorial that will work.  I share my printer hooked up to an Ubuntu Feisty desktop and share it with Windows machines.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

Remember to give the PC sharing the printer a static IP on your LAN.

---

### Post by BuntuFreak on 2008-01-26
All right help me with Gutsy. I don't see "Global Settings" menu anywhere. Basically I need to know where to go to open port 631.

thanks much.

---

### Post by Geekkit on 2008-06-20
> **strabes said:**
> Make sure the printer is shared on the ubuntu box. Run "ifconfig" and look for the section that looks like this:
Quote:
inet addr: xxx.xx.xx.xxx
Write that IP address down. On the vista computers you can simply add the printer using an http address:
Quote:
[http://ip.of.ubuntu.box:631/printers/nameofprinter](http://ip.of.ubuntu.box:631/printers/nameofprinter)

Over a year old but this post saved my sanity ... Thanks!!!

Edit: ... been finding out over the last three days that vista is truly the spawn of satan.

---

