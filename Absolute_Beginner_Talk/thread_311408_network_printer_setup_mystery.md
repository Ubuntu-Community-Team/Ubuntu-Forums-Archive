---
title: "network printer setup mystery"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by bosconermal on 2006-12-02
I am having problems setting up my HP Laserjet 5m printer as a network printer. I'm communicating via a wireless card to a printer connected directly to the router. A Windows XP2 box is also connected to the router and it prints fine.

I've followed this method from another thread:

1) add new printer as a network printer
2) pick Unix Printer
3) enter the IP address of the printer in Hosts (I got this from a printer configuration page)
4) put lpd in the queue
5) pick Laserjet 5m from the list. The driver listed below is "Postscript (recommended) (suggested)

So far so good.

When I print a test page it lists a page in the queue and releases it as though it printed, but it doesn't actually print.

I can ping the printer, so we're communicating, but no result. I got it working under Dapper but several months ago, but the machine recently got nuked and I ended up reformatting and installing with Edgy. I can't figure out how I got it to work before. Any words of wisdom?

---

### Post by steve.horsley on 2006-12-03
My guess is that you want to 1) add new printer as a network printer
2) pick HP Jet Direct
3) enter the IP address of the printer in Host: Leave the pPort as 9100

---

### Post by bosconermal on 2006-12-03
Thanks. Tried that and the print job does not clear. All I get is "printer stopped." If I resume printing, it reverts to printer stopped again.

---

### Post by DungaDunga on 2006-12-17
Have the same problem with the same printer. Same result...

---

### Post by jamesr on 2006-12-17
I have a similar problem with  Laserjet 5P.

I have tried as LPD, ipp etc etc to no avail. What type of router/printer buffer? Mine is a GVC and they recommend lpd setup but it just, does not seem to work. You are not alone. I equally would like an answer.

---

### Post by bosconermal on 2006-12-22
My router is a Linksys WRT54GS, v2.07.1 (Wireless-G Broadband Router with SpeedBooster). I struggled mightily to get this to work in the first place because it uses a Broadcom chipset. Got past that and now I've got the Internet working, but no printing.

---

