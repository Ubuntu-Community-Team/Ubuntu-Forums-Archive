---
title: "Figured out Samba/Cusp print sharing (YES!)...but something is not 100% correct"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by linux_convert on 2006-12-18
Hi,

I've been waiting a long time to have time to try out linux, but now I have, and I like it a lot.  After a few attempts, I finally figured out how to install the desktop, add the samba server, configure it as a file server, set up a printer, and share it.  I've configured samba and cusp according to the instructions from different websites.  It works (but not well).

First: I loved the challenge and the thrill of figuring things out.  I've missed this.  On Windows...I would just get annoyed when things didn't work. Sorry to be wasting everyone's time with my emotions...but IT'S SO EXCITING TO ME!

Ok, ok....here is my problem:

Printing works from XP, but it takes about 30 seconds from the time I press the "Print Test Page" button on the windows machine until the printing starts.  I can see in the System Monitor on my linux box that cusp is "working" on stuff.  I can also see a lot of activity on the LAN.  I'm concerned that a small print job takes so long and generates so much traffic.  While I'm waiting for the print job, the XP machine seems "frozen."

My setup:

Linux box is an old AMD 1Ghz PC, 100Mbps LAN cable, running Dagger Desktop.
Windows XP Laptop is also connected direct to the LAN via cable.  Both are connected directly to the cable router.  Both are in the same workgroup, I can browse each from the other, the linux shares work well, everything seems fine and dandy.

Any help is greatly appreciated and sorry for my Newbie enthusiasm.

Linux_convert

---

### Post by kd7swh on 2006-12-18
Your problem seems strange. If the two computers were on differing routers you could use a switch(es) to speed up the traffic. What type of traffic is it that is going across your LAN? Have you used wireshark to look at the packets? It might not be cups traffic slowing you down. 

You said it was a cable modem? Could other people be slowing you down? Are you downloading via bit torrent?

---

### Post by linux_convert on 2006-12-18
Hi,

It's a fairly simple set-up, with only the linux box and two xp boxes sitting on a LAN.  At the moment, there is no other network traffic.  My XP box and linux box are right next to each other, I can see the network traffic starts when I press the "print" botton on the XP box and ends when the printjob prints.

Another curious thing.  Even though I can print, when I look at the printers dialog in XP, the status of the printers shared from my linux box is: Access denied, unable to connect.

I've tested the throughput when I place files from the xp box to/from the linux box and things are very fast.

Any ideas what could be going on?

---

### Post by tagra123 on 2007-01-06
in /etc/samba/cmb.conf

look for this section

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

Add this after create mode = 0700
   use client driver = yes

so the new entry look like this

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700
   use client driver = yes

---

