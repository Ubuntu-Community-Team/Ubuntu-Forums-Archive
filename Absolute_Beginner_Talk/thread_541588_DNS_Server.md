---
title: "DNS Server"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by RobUK on 2007-09-03
Hi all,

Having got my Ubuntu server 7.04 install to recognise its nic with the help of the folks on here, I've been wading through the Apache docs regarding virtual hosts - specifically, name-based virtual hosts.

The plan is to use the Ubuntu server box (PIII 600 / 128Mb RAM / 13Gb HDD) as a local database / web server, on which will live several local websites.

I gather from the Apache docs and:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Setup_BIND_DNS_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Setup_BIND_DNS_Server)

that to get name based virtual hosts to work, I need to run a local DNS server that sends traffic for the local sites to server, and passes everything else on to my ISP's DNS servers. So far, so good (in theory - I haven't actually tried to do it yet!)

It will need to service anywhere up to 10 client machines on the local workgroup.The question is, where to set up the local DNS server?

Would it be better to set up another Ubuntu server box to act as the DNS server, or should the existing LAMP setup be able to handle it without any significant performance impact - maybe with more RAM?

If another box is advisable, what sort of minimum spec should I be looking at? I have several old Pentium 1s around that could be pressed into service, an old 486 gathering dust somewhere, and probably enough stray bits and pieces to cobble together a working PII.

Apologies in advance if this is a dumb question, but I've never needed to run a DNS server before so I've no idea how much power it's going to need.

TIA

Rob.

---

### Post by irish_flu on 2007-09-03
The DNS server footprint will be very minimal, compared to Apache and your database server.  Since you're asking though,  I would add more RAM if you can.

---

### Post by RobUK on 2007-09-03
Thanks for that. I'll pop in another 128Mb, and then have a go with running the DNS server on the PIII alongside Apache.

Rob.

---

