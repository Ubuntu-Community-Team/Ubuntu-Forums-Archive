---
title: "No print capability"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-05-01
I just installed Feisty(64) and everything works... Everything, that is, except the printer. I have an HP LaserJet 2600n which is pluged into a Netgear dual speed hub.  My two Windows machines print to the printer just fine - but I do not know how to find it from my Ubuntu machine.  Can anyone help me?? I have read all the threads on this forum regarding this printer and I am still at a loss.  How do I find the printer's URI or IP address or hostname? Being a total newby, I do not know where to begin.  I can't get the computer to auto detect the printer.

---

### Post by nanotube on 2007-05-01
well, log into your router, and look at the status info - one of the IPs should be assigned to a printer.

also, you could do an nmap on your local subnet - will spit out all IPs that are in use by various things on your subnet.

---

### Post by WhiteSphinx on 2007-05-01
I don't have a router. I am connecting all my computers and printer via a seven port "hub".  I don't know how to do an nmap.  I am not a techie - I'm just an average Joe.

---

### Post by Seisen on 2007-05-01
Can you hook it up to your ubuntu computer using a usb cable?

---

### Post by nanotube on 2007-05-01
> **WhiteSphinx said:**
> I don't have a router. I am connecting all my computers and printer via a seven port "hub".  I don't know how to do an nmap.  I am not a techie - I'm just an average Joe.

what's the hub connected to? in other words, what actually assigns IP addresses?

---

### Post by WhiteSphinx on 2007-05-01
> **Seisen said:**
> Can you hook it up to your ubuntu computer using a usb cable?

Okay! Hooking up with the usb cable worked and I can still print from my other computers as well.  Now if I could just get Ubuntu to print color.  I set the color mode to color, but it still just prints monochrome.

---

### Post by WhiteSphinx on 2007-05-01
Success!!!  I downloaded the driver from [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/) and then edited the ppd (at /etc/cups/ppd/) so that the FoomaticRIPCommandLine read thus:
FoomaticRIPCommandLine: "foo2hp2600-wrapper -c %A"

I found this info on another forum. It works on a test print. Now I'm going to print some photos and see what happens.

---

