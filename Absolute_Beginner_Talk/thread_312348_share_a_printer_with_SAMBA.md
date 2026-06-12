---
title: "share a printer with SAMBA"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by dann0 on 2006-12-04
I'm having trouble connecting to a printer-share in SAMBA.
The printer is working OK on local computer, and I can see it from my other machine. But I can't print to it from the second computer.

I have a network that include windows systems, that's why I use samba.

Please help me...

---

### Post by mitch.c on 2006-12-04
> **dann0 said:**
> I'm having trouble connecting to a printer-share in SAMBA.
The printer is working OK on local computer, and I can see it from my other machine. But I can't print to it from the second computer.

I have a network that include windows systems, that's why I use samba
I'm assuming your printer is connected to you ubuntu machine? Are you using samba only for printing? If that's the case, I've found it's much easier to dump samba and simply use cups native ipp printing to print from windows to a  ubuntu machine.

If you want to try, see this post: [http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2)

One important note: These instructions were written for dapper... if you are using edgy, the Listen directives listed will be found in /etc/cups/cupsd.conf

---

### Post by dann0 on 2006-12-04
Hi!
Thanks a lot! that really helped.

can one use this AND samba ?

---

### Post by mitch.c on 2006-12-04
> **dann0 said:**
> can one use this AND samba ?
Absolutely. If you need samba for something else, use it. I only recommend cups ipp printing as an alternative to installing and configuring samba for printing only.

So often I see people struggling to configure samba for printing, when cups is all they need...

[LIST]
[*]Cups is installed be default.
[*]Cups has native IPP printing.
[*]Windows supports printing via IPP.
[*]Configuration is minimal (amounts to telling cups to listen on network interface).
[/LIST]

---

### Post by dann0 on 2006-12-04
Thanks for the answer, now I can print from network connected windows and ubunt machines.
I also made a note to self that the PPD-files for the printer must be installed.

---

