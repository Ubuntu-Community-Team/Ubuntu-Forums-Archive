---
title: "Evolution IMAP with custom ports?  How do I set that up in 7.10?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-03-23
Hi,

I am using Sherweb.com as my exchange host.  Since Exchange 2007 doesnt work with Evolution, I want to try using Imap instead. 

I set everything up but the ISP wants to use custom ports.  I am playing with the mail settings for the IMAP account I setup, but I dont see where to put in the ports (I see no encryption, TSL or SSL).  

Any ideas on how to do that?

Thanks,
Rich



Here is the info:

Here the setting to use:

IMAP Server: webmail.ihostexchange.net
Username: Your SAM Account name. You have this information in your MS Exchange Control Panel (Ex: user_domain.com) See the print screen for more information.
Password: Your password
Port: 993 (using SSL)

SMTP Server: smtp.ihostexchange.net
Username: Your SAM Account name. You have this information in your MS Exchange Control Panel (Ex: user_domain.com) See the print screen for more information.
Password: Your password
Port: 587 (using SSL for Outlook 2003 and TLS for Outlook 2007)
Require Authentication: Yes. Use same settings as your incoming mail server.

---

### Post by plucky on 2008-03-24
> I set everything up but the ISP wants to use custom ports. I am playing with the mail settings for the IMAP account I setup, but I dont see where to put in the ports (I see no encryption, TSL or SSL).
Any ideas on how to do that?

Like this```
 webmail.ihostexchange.net:993
``` and ```
smtp.ihostexchange.net:587
```

Good Luck

---

