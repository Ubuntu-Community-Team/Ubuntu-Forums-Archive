---
title: "eFax Error: Can't open pre-lock file...."
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by vgrisham on 2007-03-17
Hi,

I am trying to send a fax from OpenOffice in Ubuntu Dapper, and I get this error message: efax-0.9a: 27:22 Error: can't open pre-lock file /var/lock/LCK../dev/TMP..09575: No such file or directory 
 
Have I missed something in the configuration? 
 
I'm using Linuxant, and the modem seems to be communicating. I paid for the full license, and the key is entered. The registration status shows as OK. The modem will dial out when I try to activate it in networking to dial an ISP.  
 
lspci shows me this: 0000:05:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01) 
 
Thanks, 
 Vaughn

---

### Post by vgrisham on 2007-03-17
Well, I blew away the version from Synaptic and then compiled the newest version from source. That did the trick. Problem solved. eFax is working like a charm now. :guitar:

---

