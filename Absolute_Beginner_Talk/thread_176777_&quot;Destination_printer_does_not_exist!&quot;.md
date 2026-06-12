---
title: "&quot;Destination printer does not exist!&quot;"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-15
I have done everyting in the forums and wiki that I can find and it seems that my laptop with Ubuntu breezy can finally see my server with Ubuntu dapper.

But the laptop still get this printing errors when I try to print:

"Destination printer does not exist!"

and the server cups error log says:

Get-Printer-Attributes client-error-not-found: The printer or class was not found.

Ok then went into the laptop settings and changed the printer address from ipp to hpdirect and host ip port 631.
Now the server says:

I [15/May/2006:08:26:42 -0400] Generating server key...
E [15/May/2006:08:26:43 -0400] Unable to create server key file "/etc/cups/ssl/server.key" - No such file or directory
E [15/May/2006:08:26:43 -0400] encrypt_client: Unable to encrypt connection from 192.168.1.104!
E [15/May/2006:08:26:43 -0400] encrypt_client: A record packet with illegal version was received.

Any ideas?

---

