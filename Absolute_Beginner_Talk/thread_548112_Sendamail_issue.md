---
title: "Sendamail issue"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by ajzone on 2007-09-10
Hello everyone

I am pretty new to Ubuntu. I have recently installed sendmail and haven been playing with it for sometime now. After a lot of changes and fixes i have been able to have sendmail "accept" messages for delivery. I have set the DeliveryMode option to be 'b'( background ). But still for some reason, all of the messages just sit in the queue. here is what was spewed in /var/log/mail.log

root@home:/home/abhi# Sep 10 22:23:41 home sendmail[3305]: l8B2NcOC003305: from=abhi, size=9, class=0, nrcpts=1, msgid=<200709110223.l8B2NcOC003305@home>, relay=root@localhost
Sep 10 22:23:41 home sm-mta[3308]: l8B2Nfc7003308: from=<abhi@home>, size=284, class=0, nrcpts=1, msgid=<200709110223.l8B2NcOC003305@home>, proto=ESMTP, daemon=MSP-v4, relay=localhost.localdomain [127.0.0.1]
Sep 10 22:23:41 home sendmail[3305]: l8B2NcOC003305: to=ajzone@gmail.com, ctladdr=abhi (1000/1000), delay=00:00:03, xdelay=00:00:00, mailer=relay, pri=30009, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (l8B2Nfc7003308 Message accepted for delivery)

running mailq gives me this 

MSP Queue status...
/var/spool/mqueue-client is empty
                Total requests: 0
MTA Queue status...
                /var/spool/mqueue (1 request)
-----Q-ID----- --Size-- -----Q-Time----- ------------Sender/Recipient-----------
l8B2Nfc7003308*       9 Mon Sep 10 22:23 <abhi@home>
                                         <ajzone@gmail.com>
                Total requests: 1

I am just stuck here. Can anyone suggest what should i be doing to get it to working?

Thanks
AJ

---

### Post by bwhitaker on 2007-09-10
I could be wrong, I haven't used actual sendmail in about 8 years, but I think your server is trying to use itself as a smart host.  So, it's sending messages to itself to delivery, you'll probably need to have it use your ISP's mail server as a relay 

This might help in configuring a smart host, scroll about half way down:

[http://www.faqs.org/docs/linux_network/x15291.html](http://www.faqs.org/docs/linux_network/x15291.html)


Also I'd recommend using postfix instead of sendmail.  It's more secure and easier to use.

---

### Post by ajzone on 2007-09-11
I tried settting the SMART_HOST macro to smtp.comcast.net. But still have the same issue. Thanks for the link it was very informational. 

Anything else I can do before I give up and try Postfix?

---

