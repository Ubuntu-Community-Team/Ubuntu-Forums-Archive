---
title: "Linksys wireless printserver"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-26
I am thinking about moving my HP LaserJet onto my network. I am looking at a Linksys Wireless Printserver model WPS54G. Has anyone used one of these successfully with Ubuntu 6.06?

---

### Post by cilynx on 2006-07-26
I've never used that device proper, but I have used much of the Linksys line and have had no problems what-so-ever.

Doing a quick google search, it looks like the WPS54G is not-so-much happy to work with Linux.  I would look elseware.

Why not just drop the LJ directly onto your Ubuntu box and share it from there?  What model of LJ is it?  They are very different...

---

### Post by OU812 on 2006-07-27
This might help.

[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

john

---

### Post by OU812 on 2006-07-28
I just got my canon i560 to work with a netgear wgps606 printserver. Here's a few things I did to get it to work:

1. I looked at the link I gave you to find a linux driver for the canon i550 (the printserver won't work with the i560 so I use i550 drivers).
2. Then I did a google search with the keywords "netgear wgps606 linux" and found a guide.
3. I had trouble using [http://localhost:631/admin](http://localhost:631/admin) so I used kubuntu tools to add the printer.
4. Basically the option you want is "LPD/LPR Host or Printer" and the URI is uri://<your_wgps606_ip>/L1.
5. You may have to make sure you are part of the lpadmin group. (I'm not sure if I did it correctly, but I know I tried. It works so maybe!)

I know I have a different brand than you and maybe a different ubuntu, but I think some of these experiences may apply.

john

---

### Post by fmorriso on 2007-11-03
On November 3, 2007, the only way I could get Ubuntu 7.10 to connect to my HP 6L printer that in turn is connected to my LinkSys WPS54G print server was to (1) change the printers IP address from variable (via DHCP) to fixed (192.168.2.90 in my case) and (2) manually type in the following into the "Other" printer setup dialog (based upon other posts I saw earlier) ipp://192.168.2.90/ipp/P1.   Since I'm an absolute beginner with Ubuntu, I figured such arcane ways of connecting printers in Linux is no worse than hacking the Registry in Windows to make things work.  Maybe someday, Ubuntu (and Linux) won't need to mimic the bad parts of Windows in order to connect to a wireless printer via a printer server?

---

### Post by zzandeamos on 2007-11-28
Fred;
How did you determine what your IP address was?  I have a WPS54G that works fine with two win machines but cant get it to work with Ubuntu.  The IP address that resulted from my other machines was 192.168.0.73, would I use that?  AND just where do I put it in? 
Thanks  Frank

Resolved...
Thanks to all I have resolved this problem.  Now I can print from any of three machines (two xp and one Ubuntu) to one printer.
Works great.
FDC

---

### Post by gyrene2083 on 2007-12-18
I'm curious to know how to install the Linksys wps54g print server. I've had it running for several months on a few windows laptops, but now I made the conversion to Linux, (which  I'm quite happy about, by the way), and I'm not sure how to install windows apps. 

Do I have to use the ndiswrapper?

---

