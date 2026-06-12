---
title: "Hylafax Help"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by jeffw on 2007-09-05
Help

I am new to Ubuntu.

I have installed version 7.04 and wish to setup Hylafax to receive faxes and send to end-user via email

I have got it working except either Hylafax or Postfix is truncating or corrupting the tiff file sent via email.

Tiff in /var/spool/hylafax/recvq is perfect but when it arrives via email  the tiff file is only 268 bytes.

I am using Postfix which is forwarding to MS Exchange 2003 SMTP host.

Any help would be appreciated.

---

### Post by Bremenacht on 2007-11-08
Slight thread hijack here (sorry jeffw) but does anyone know whether hylafax can accept incoming faxes on two or more lines? It's sort of implied in the Hylafax handbook, but it's not explicit.

I'm assuming I'd have to run an instance of 'faxgetty' for each modem.

Ta,

Brem

---

