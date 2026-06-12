---
title: "Thunderbird, smtp connection failed"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-03-01
Hi,

I use thunderbird to see gmail emails for a while. I moved to a different place with different wireless connection and for some reason I cannot sent emails anymore (I ca
n get emails). After I press send button, system waits but without sending email and at the end it gives following error:
[I]The message could not be sent because connecting to smtp server smtp.gmail.com failed. The server may be refusing SMTP connections...
[/I]
I also closed firewall, but still no connection. Any suggestions why this happened?

thanks
findik

---

### Post by dstew on 2007-03-01
If you have changed locations, you may now be using the services of a different ISP (internet services provider). Different ISP's have different rules for using SMTP. The new ISP may want you to use their own SMTP server, and not let you use gmail's. They do this to prevent spam. Alternatively, gmail may not accept SMTP requests from your new ISP for the same reason. For example, I have Verizon as my ISP, and I can receive messages from an outside POP account, but I have to use the outgoing Verizon SMTP server to send mail, even though my other email provider has SMTP service.

To fix the problem of sending, you may need to have an account and password to use the ISP's SMTP services. Or, you just need to go to gmail on the web, and bypass Thunderbird.

---

### Post by actuary286 on 2007-03-01
Here is a tutorial on setting up GMail with Thunderbird:
[URL="http://email.about.com/od/mozillathunderbirdtips/qt/et121604.htm"]
http://email.about.com/od/mozillathunderbirdtips/qt/et121604.htm[/URL]

I have a similar problem with my university email account's smtp and my ISP's port blocking. Try using the port listed in the tutorial instead of the default port 25.

---

