---
title: "Exim and Outlook"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-13
Hi

Is it possible to have Outlook send/fetch mail from exim4 (or something that works together with exim4)?  I have to use Windows on my laptop because ViaVoice (I use it a lot in my work) does not have a Linux equivalent. 

If it is possible, please tell me how to do this.  If it can't be done, I've wasted about 6 weeks trying to Ubuntu!

---

### Post by mlentink on 2007-07-13
Hmmm. Isn't Exim a MTA (=Mail Transfer Agent), like Postfix? If so, you would need a MDA (=Mail Delivery Agent) for Outlook to be able te exchange mail with it.
My homeserver runs Postfix as MTA (this is sort of the standard in Ubuntu) and I use Dovecot as MDA. 

Since Dovecot serves standard POP3 and IMAP protocols, having your Outlook clients connect to it is a no-brainer.

---

### Post by Amplidude on 2007-07-13
> **mlentink said:**
> Hmmm. Isn't Exim a MTA (=Mail Transfer Agent), like Postfix? If so, you would need a MDA (=Mail Delivery Agent) for Outlook to be able te exchange mail with it.
My homeserver runs Postfix as MTA (this is sort of the standard in Ubuntu) and I use Dovecot as MDA. 

Since Dovecot serves standard POP3 and IMAP protocols, having your Outlook clients connect to it is a no-brainer.

Thanks - you and half a dozen Valium have staved off a major panic attack.  What are the MDA's available out there, and which would you suggest for use with Exim4 (Or should I replace Exim4 - whatever I use has to be able to integrate with an email discussion manager)

Beautiful person... or is that the Valium kicking in?

---

